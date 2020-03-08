<template>
  <div class="container mx-auto">
    <div class="area-container">
      <nuxt-link :to="'/area/' + areas.id" v-for="areas in areas" :key="areas.id" class="block mb-8">
        <img class="thumb" :src="areas.ensignUrl" alt="flag">
        <div>{{ areas.name }}</div>
        <div>{{ areas.parentArea }}</div>
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
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.thumb{
  height: 50px;
  width: 50px;
  border-radius: 50%;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
