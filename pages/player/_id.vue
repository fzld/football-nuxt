<template>
    <div class="container mx-auto">
        <div class="player-container">
            <div class="block mb-8">
                <div>{{ player.name }}</div>
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