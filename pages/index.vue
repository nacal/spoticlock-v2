<template>
  <div
    class="grid justify-center content-between min-h-screen w-full bg-gradient-to-t from-green-900 to-primary p-2"
  >
    <header>
      <h1 class="font-bold text-5xl text-center text-gray-900 mb-2 mt-8">
        SpotiClock
      </h1>
      <p class="text-xs md:text-base text-center text-gray-900 mb-4">
        A clock that shows the nowplaying song on spotify.
      </p>
      <Button />
    </header>
    <main>
      <MusicPlayerCard :now-playing="nowPlaying" />
    </main>
    <footer class="text-center">
      <small lang="en">&copy; 2021 nacal</small>
    </footer>
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
