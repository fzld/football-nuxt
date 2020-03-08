<template>
    <div class="container mx-auto py-16 p-6">
        <div class="team-container text-center">
                <img class="logo mx-auto" :src="team.crestUrl" alt="logo">
                <div class="text-black font-semibold text-lg overflow-hidden whitespace-no-wrap overflow-dots">{{ team.name }}</div>
                <div>Founded in {{ team.founded }}, {{ team.area.name }}</div>
                <div>{{ team.venue }}</div>
                <div>{{ team.address }}</div>
                <div>{{ team.phone }}</div>
                <div>{{ team.website }}</div>
                <br><br><br>
                <div class="text-black font-semibold text-lg overflow-hidden whitespace-no-wrap overflow-dots">{{ team.name }}'s Squads</div>
                <br>
        </div>
        <div class="squad-container">
                <nuxt-link :to="'/player/' + squad.id" v-for="squad in team.squad" :key="squad.id" class="block mb-8">
                <div class="bg-gray-200 hover:bg-gray-900 text-black hover:text-white font-bold py-2 px-4 rounded">{{ squad.name }}</div>
                <div class="bg-gray-500 text-white font-bold py-2 px-4 rounded">{{ squad.position }}</div>
                </nuxt-link>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    asyncData ({ params, error }) {
    return axios.get(`https://api.football-data.org/v2/teams/${params.id}`)
      .then((res) => {
        return {
          team: res.data
          }
      })
      .catch((e) => {
        console.log(e)
      })
  }
}
</script>