<template>
  <div id="clock" :style="{ backgroundColor: hexTime }">
    <span>{{ hexTime }}</span>
  </div>
</template>

<script>
export default {
  name: 'clock',
  data () {
    return {
      hexTime: this.getHexTime()
    }
  },
  methods: {
    getHexTime () {
      // Get the time and set segments
      let now = new Date(Date.now());
      let hour = `${now.getHours()}`;
      let minute = `${now.getMinutes()}`;
      let second = `${now.getSeconds()}`;

      // Zero fill each segment if needed
      if (hour.length === 1) {
        hour = `0${hour}`;
      }

      if (minute.length === 1) {
        minute = `0${minute}`;
      }

      if (second.length === 1) {
        second = `0${second}`;
      }

      return `#${hour}${minute}${second}`
    },
  },
  mounted () {
    setInterval(() => {
      this.hexTime = this.getHexTime()
    }, 1000);
  }
}
</script>

<style scoped>
  #clock {
    font-size: 10rem;
    color: #eaf6e5;
    grid-column: span 12;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>