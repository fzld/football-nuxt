<template>
  <div class="container mx-auto py-16 grey-200">
    <div class="area-container flex flex-wrap -mx-4 bg-grey-200">
      <div>
      </div>
      <nuxt-link :to="'/area/' + areas.id" v-for="areas in areas" :key="areas.id" class="w-full md:w-1/5 px-4 mb-12 no-underline">
        
        <div class="bg-gray-200 hover:bg-gray-900 text-black hover:text-white font-bold py-2 px-4 rounded">{{ areas.name }}</div>
        <div class="text-grey-darker text-base overflow-hidden whitespace-no-wrap overflow-dots pb-1">{{ areas.parentArea }}</div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'

export default {
  components: {
    Logo
  },
  asyncData ({ params, error }) {
    return axios.get(`https://api.football-data.org/v2/areas/`)
      .then((res) => {
        return {
          areas: res.data.areas
          }
      })
      .catch((e) => {
        console.log(e)
      })
  },
  data() {
    return {

    }
  },
  head: {
    title: 'Football-data SPA',
    meta: [
      {  
      }
    ]}
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

.thumb {
  height: 100px;
  width: 100px;
}

</style>