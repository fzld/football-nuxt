<template>
    <div class="container mx-auto py-16 p-6">
      <h1 class="text-black font-semibold text-lg overflow-hidden whitespace-no-wrap overflow-dots py-16">Player Details</h1>
        <div class="player-container bg-grey-200">
            <div>
                <div class="text-black font-semibold text-lg overflow-hidden whitespace-no-wrap overflow-dots">{{ player.name }}</div>
                <div>{{ player.dateOfBirth }}</div>
                <div>{{ player.nationality }}</div>
                <div>{{ player.position }}</div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    asyncData ({ params, error }) {
    return axios.get(`https://api.football-data.org/v2/players/${params.id}`)
      .then((res) => {
        return {
          player: res.data
          }
      })
      .catch((e) => {
        console.log(e)
      })
  }
}
</script>