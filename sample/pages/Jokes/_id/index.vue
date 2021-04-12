<template>
  <div>Single Joke: {{ joke }}</div>
</template>

<script>
import axios, { AxiosResponse } from 'axios'

export default {
  data() {
    return {
      joke: {},
    }
  },
  async created() {
    const config = {
      headers: {
        Accept: 'application/json',
      },
    }
    try {
      const str = `https://icanhazdadjoke.com/j/${this.$route.params.id}`
      console.log(str)
      const res = await axios.get(str, config)
      this.joke = res.data.joke
    } catch (err) {
      console.log(err)
    }
  },
}
</script>