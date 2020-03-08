<template>
    <div class="container mx-auto">
        <div class="team-container">
            <div class="block mb-8">
                <img :src="team.crestUrl" alt="logo">
                <div>{{ team.name }}</div>
                <div>Founded in {{ team.founded }}, {{ team.area.name }}</div>
                <div>{{ team.venue }}</div>
                <div>{{ team.address }}</div>
                <div>{{ team.phone }}</div>
                <div>{{ team.website }}</div>
                <br><br><br>
                <div>{{ team.name }}'s Squads</div>
                <br>
                <nuxt-link :to="'/player/' + squad.id" v-for="squad in team.squad" :key="squad.id" class="block mb-8">
                <div>{{ squad.name }}</div>
                <div>{{ squad.position }}</div>
                </nuxt-link>
            </div>
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