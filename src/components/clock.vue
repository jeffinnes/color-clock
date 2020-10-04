<template>
  <div :style="{ backgroundColor: hexTime }">
    <h1>{{ hexTime }}</h1>
  </div>
</template>

<script>
export default {
  name: 'clock',
  data () {
    return {
      hexTime: '#000000'
    }
  },
  mounted () {
    setInterval(() => {
      // Get the time and set segments
      let now = new Date(Date.now());
      let hour = `${now.getHours()}`;
      let minute = `${now.getMinutes()}`;
      let second = `${now.getSeconds()}`;

      // Zero fill each segment if needed
      if (hour.length === 1) {
        hour += `0${hour}`;
      }

      if (minute.length === 1) {
        minute += `0${minute}`;
      }

      if (second.length === 1) {
        second += `0${second}`;
      }

      this.hexTime = `#${hour}${minute}${second}`
    }, 1000);
  }
}
</script>

<style scoped>

</style>