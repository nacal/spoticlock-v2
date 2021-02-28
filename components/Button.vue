<template>
  <div class="flex justify-center">
    <button
      class="btn-primary bg-gray-900 hover:bg-gray-800 text-white mr-2"
      @click="spotifyLogin()"
    >
      Login
    </button>
    <button
      class="btn-primary bg-gray-200 hover:bg-gray-300"
      @click="getNowPlaying()"
    >
      Start
    </button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  beforeCreate() {
    if (this.$route.hash) {
      this.$router.push(this.$route.fullPath.replace('#', '?'))
    }
  },
  methods: {
    spotifyLogin() {
      const endpoint = 'https://accounts.spotify.com/authorize'
      const responseType = 'token'
      const clientId = process.env.apiKey
      const redirectUri = process.env.baseURL
      const scope = 'user-read-currently-playing'
      location.href =
        endpoint +
        '?response_type=' +
        responseType +
        '&client_id=' +
        clientId +
        '&redirect_uri=' +
        redirectUri +
        '&scope=' +
        scope
    },
    getNowPlaying() {
      const endpoint =
        'https://api.spotify.com/v1/me/player/currently-playing?market=JP'
      const data = {
        headers: {
          Authorization:
            this.$route.query.token_type + ' ' + this.$route.query.access_token,
        },
        data: {},
      }
      const self = this
      const fetchData = function () {
        axios
          .get(endpoint, data)
          .then((res) => {
            self.$parent.nowPlaying = res.data
          })
          .catch(() => {})
      }
      fetchData()
      setInterval(fetchData, 1000)
    },
  },
}
</script>

<style lang="postcss" scoped>
.btn-primary {
  @apply py-2 w-32 shadow-md no-underline rounded-full text-sm transition duration-500;
}
</style>
