<template>
  <div class="px-3 mx-auto">
    <input
      v-model="searchQuery"
      type="text"
      placeholder="Search your fav artiste..."
      class="md:w-2/5 w-full px-4 py-2 rounded-md border border-gray-300 shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
      @input="debouncedSearch"
    />
    <FeaturedEvent :searchResults="searchResults" />
    <AllEvents :searchResults="searchResults" />
  </div>
</template>

<script>
import axios from 'axios'
import { debounce } from 'lodash'
import FeaturedEvent from './FeaturedEvent.vue'
import AllEvents from './AllEvents.vue'

export default {
  components: {
    FeaturedEvent,
    AllEvents
  },
  // Passing the searchQuery and searchResults as data
  data() {
    return {
      searchQuery: '',
      searchResults: []
    }
  },
  mounted() {
    // Fetch the data from the API on page load (default artiste is Ed Sheeran)
    axios
      .get(
        'https://rest.bandsintown.com/artists/ed%20sheeran/events?app_id=0ab49580-c84f-44d4-875f-d83760ea2cfe'
      )
      .then((response) => {
        this.searchResults = response.data
      })
      .catch((error) => {
        console.error('There was a problem fetching the data:', error)
      })

    // Debounce the search function
    this.debouncedSearch = debounce(this.search, 700)

    // Get the search results from localStorage
    this.searchResults = JSON.parse(localStorage.getItem('searchResults') || '[]')
  },
  methods: {
    // Search function
    async search() {
      // Check if the search query is empty
      if (this.searchQuery === '') {
        return
      }

      try {
        const response = await axios.get(
          `https://rest.bandsintown.com/artists/${this.searchQuery}/events?app_id=0ab49580-c84f-44d4-875f-d83760ea2cfe`
        )

        // Set the search results to the response data
        this.searchResults = response.data

        // Set the search results to localStorage
        localStorage.setItem('searchResults', JSON.stringify(this.searchResults))
      } catch (error) {
        console.error(error)
      }
    }
  }
}
</script>

<style scoped></style>
