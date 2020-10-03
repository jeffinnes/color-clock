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
      let now = new Date(Date.now());
      this.hexTime = `#${now.getHours()}${now.getMinutes()}${now.getSeconds()}`
    }, 1000);
  }
}
</script>

<style scoped>

</style>