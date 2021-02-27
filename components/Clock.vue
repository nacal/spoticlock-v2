<template>
  <div class="text-right flex flex-col justify-between">
    <p class="text-white text-xs">{{ date }}</p>
    <p class="text-white text-3xl leading-none numbers">{{ time }}</p>
  </div>
</template>

<script>
export default {
  name: 'Clock',
  data() {
    return {
      date: '',
      time: '',
      week: ['Sun.', 'Mon.', 'Tue.', 'Wed.', 'Thu.', 'Fri.', 'Sat.'],
    }
  },
  mounted() {
    setInterval(this.updateTime, 1000)
  },
  methods: {
    updateTime() {
      const currentDate = new Date()
      this.time =
        this.zeroPadding(currentDate.getHours(), 2) +
        ':' +
        this.zeroPadding(currentDate.getMinutes(), 2) +
        ':' +
        this.zeroPadding(currentDate.getSeconds(), 2)
      this.date =
        this.zeroPadding(currentDate.getFullYear(), 4) +
        '-' +
        this.zeroPadding(currentDate.getMonth() + 1, 2) +
        '-' +
        this.zeroPadding(currentDate.getDate(), 2) +
        ' ' +
        this.week[currentDate.getDay()]
    },
    zeroPadding(num, len) {
      let zero = ''
      for (let i = 0; i < len; i++) {
        zero += '0'
      }
      return (zero + num).slice(-len)
    },
  },
}
</script>

<style lang="postcss">
.numbers {
  font-feature-settings: 'tnum';
  font-variant-numeric: tabular-nums;
}
</style>
