<template>
  <div
    class="grid place-items-center min-h-screen bg-gradient-to-t from-green-900 to-primary p-5"
  >
    <Button />
    <MusicPlayerCard :now-playing="nowPlaying" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      nowPlaying: {
        item: {
          artists: [
            {
              name: 'artist',
            },
          ],
          name: 'music title',
          album: {
            images: [
              {},
              {
                url:
                  'https://upload.wikimedia.org/wikipedia/en/f/f1/Tycho_-_Epoch.jpg',
              },
            ],
          },
        },
      },
    }
  },
}
</script>
