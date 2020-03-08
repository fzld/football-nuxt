<template>
    <div class="container mx-auto">
    <div class="competitions-container">
        <div class="block mb-8">Here is the list of Teams in this Area</div>
      <nuxt-link :to="'/teams/' + teams.id" v-for="teams in teams" :key="teams.id" class="block mb-8">
        <div>{{ teams.name }}</div>
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