<template>
    <div class="container mx-auto">
        <div class="player-container bg-grey-200">
            <div class="text-center">
                <img class="h-16 w-16 rounded-full mx-auto" src="/assets/img/player.png">
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