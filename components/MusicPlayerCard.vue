<template>
  <article class="max-w-full md:w-96">
    <div v-if="nowPlaying != ''" class="bg-gray-900 shadow-lg rounded p-3">
      <div class="relative">
        <img
          class="max-w-full md:w-96 block rounded"
          :src="nowPlaying.item.album.images[1].url"
          alt=""
        />
      </div>
      <div class="p-5 flex justify-between">
        <div class="w-32 md:w-3/5">
          <h3 class="text-white text-lg truncate">
            {{ nowPlaying.item.name }}
          </h3>
          <p class="text-gray-400 truncate">
            {{ nowPlaying.item.artists[0].name }}
          </p>
        </div>
        <Clock class="md:w-2/5" />
      </div>
    </div>

    <div v-else class="bg-gray-900 shadow-lg rounded p-3">
      <div class="relative">
        <img
          class="w-full md:w-96 block rounded"
          src="https://upload.wikimedia.org/wikipedia/en/f/f1/Tycho_-_Epoch.jpg"
          alt=""
        />
      </div>
      <div class="p-5 flex justify-between">
        <div class="w-32 md:w-3/5">
          <h3 class="text-white text-lg truncate">Not Found.</h3>
          <p class="text-gray-400 truncate">ERROR</p>
        </div>
        <Clock class="md:w-2/5" />
      </div>
    </div>
  </article>
</template>

<script>
export default {
  props: {
    nowPlaying: {
      type: Object,
      required: true,
    },
  },
}
</script>
