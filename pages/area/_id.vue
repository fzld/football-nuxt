<template>
    <div class="container mx-auto bg-grey-200">
    <h1 class="text-black font-semibold text-lg overflow-hidden whitespace-no-wrap overflow-dots text-center">Here is the list of Teams in this Area</h1>
    <div class="competitions-container text-center">
        <div class="block mb-8"></div>
        <nuxt-link :to="'/teams/' + teams.id" v-for="teams in teams" :key="teams.id" class="block mb-8">
          <div class="bg-gray-200 hover:bg-gray-900 text-black hover:text-white font-bold py-2 px-4 rounded">{{ teams.name }}</div>
        </nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    asyncData ({ params, error }) {
    return axios.get(`https://api.football-data.org/v2/teams?areas=${params.id}`)
      .then((res) => {
        return {
          teams: res.data.teams
          }
      })
      .catch((e) => {
        console.log(e)
      })
  }
}
</script>