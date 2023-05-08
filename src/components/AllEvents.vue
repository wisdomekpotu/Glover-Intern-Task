<template lang="">
  <div>
    <h2 class="px-6 py-6 mx-auto text-xl font-bold">All Events</h2>
    <section class="text-gray-600 body-font">
      <div class="container px-5 py-24 mx-auto">
        <div class="flex flex-wrap -m-4">
          <div
            class="lg:w-1/4 md:w-1/2 p-4 w-full"
            v-for="(event, index) in searchResults.slice(2, 10)"
            :key="index"
          >
            <div class="h-30 border-2 border-gray-200 border-opacity-60 rounded-lg overflow-hidden">
              <img
                class="lg:h-48 md:h-36 w-full object-cover object-center p-3"
                src="../assets/images/placeholder.png"
                alt="blog"
              />

              <div class="p-3">
                <h3
                  class="py-2 absolute w-105 pl-2 h-18 left-192 top-503 font-firma font-bold text-14 leading-18 text-gray-600"
                >
                  {{ event.lineup[0] }}
                </h3>
                <div class="relative">
                  <span class="float-right py-2 pr-2 inline-flex items-baseline justify-center"
                    ><img src="../assets/images/date.png" alt="" srcset="" />
                    <div
                      class="flex items-center py-2 absolute text-white text-xs"
                      style="color: #ff6a2c"
                    >
                      31 Oct
                    </div>
                  </span>
                </div>

                <div class="py-12">
                  <span class="inline-flex items-baseline text-gray-600">
                    <img
                      src="../assets/images/loc.png"
                      alt=""
                      class="self-center w-5 h-5 rounded-full mx-1"
                    />
                    <span>{{ event.venue.name }}</span>
                  </span>
                  <br />
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
                    <span class="inline-flex items-baseline">
                      <img src="../assets/images/tik.png" alt="" class="self-center w-5 h-5 mx-2" />
                      <span>Starting from <span class="text-indigo-900">₦15,000</span></span>
                    </span>
                  </div>
                  <div class="py-1">
                    <span class="inline-flex items-baseline pl-2">
                      <a :href="event.offers[0].url">
                        <button
                          class="absolute w-32 h-10 text-indigo-900 rounded-lg shadow-md focus:outline-none border border-indigo-900"
                        >
                          Buy Ticket
                        </button>
                      </a>
                    </span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
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
