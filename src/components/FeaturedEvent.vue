<template lang="">
  <h2 class="px-2 py-6 mx-auto text-xl font-bold">Featured Events</h2>
  <section class="text-gray-600 body-font">
    <div class="container px-2 py-6 mx-auto">
      <div class="flex flex-wrap -m-4">
        <!-- Use v-for directive to loop through the first two items of searchResults array -->
        <div class="p-4 md:w-1/2" v-for="(event, index) in searchResults.slice(0, 2)" :key="index">
          <div class="h-full border-2 border-gray-200 border-opacity-60 rounded-lg overflow-hidden">
            <img
              class="lg:h-48 md:h-36 w-full object-cover object-center p-3"
              alt="blog"
              src="../assets/images/wizkid.png"
            />

            <div class="p-3">
              <h3
                class="py-2 absolute w-105 pl-4 h-18 left-192 top-503 font-firma font-bold text-14 leading-18 text-gray-600"
              >
                {{ event.lineup[0] }}
              </h3>

              <div class="py-10">
                <span class="pl-3 inline-flex items-baseline text-gray-600">
                  <img
                    src="../assets/images/loc.png"
                    alt=""
                    class="self-center w-5 h-5 rounded-full mx-1"
                  />
                  <span>{{ event.venue.name }}</span>
                </span>

                <span class="py-2 inline-flex items-baseline">
                  <img src="../assets/images/sch.png" alt="" class="self-center w-5 h-5 mx-2" />
                  <span>{{
                    new Date(event.datetime).toLocaleDateString('en-US', {
                      weekday: 'short',
                      year: 'numeric',
                      month: 'short',
                      day: 'numeric'
                    })
                  }}</span>
                </span>

                <div class="py-1">
                  <span class="float-right inline-flex items-baseline">
                    <a :href="event.offers[0].url">
                      <button
                        class="w-32 h-10 text-indigo-900 rounded-lg shadow-md focus:outline-none border border-indigo-900"
                      >
                        Buy Ticket
                      </button>
                    </a>
                  </span>
                </div>
                <div class="py-3">
                  <span class="pl-2 inline-flex items-baseline">
                    <img src="../assets/images/tik.png" alt="" class="self-center w-5 h-5 mx-2" />
                    <span>Starting from <span class="text-indigo-900">₦15,000</span></span>
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  // Passing the searchResults as props
  props: {
    searchResults: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped=""></style>
