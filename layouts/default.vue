<template>
  <div>
    <navigation/>
    <nuxt />
  </div>
</template>

<script>
import Navigation from '@/components/navigation'
import axios from 'axios'

axios.defaults.headers.common['X-Auth-Token'] = '093a611a05a44c97b2dc28821bfebb07'

export default {
  components: {
    Navigation
  }
  
}
</script>