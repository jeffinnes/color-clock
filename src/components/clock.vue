<template>
  <div id="clock" :style="{ backgroundColor: hexColor }">
    <span>{{ hexTime }}</span>
  </div>
</template>

<script>
export default {
  name: "clock",
  data() {
    return {
      hexTime: '',
      hexColor: '',
      baseHour: "00",
      baseMinute: "00",
      baseSecond: "00",
    };
  },
  methods: {
    getHexTime() {
      // Get the time and set segments
      const now = new Date(Date.now());
      let hour = `${now.getHours()}`;
      let minute = `${now.getMinutes()}`;
      let second = `${now.getSeconds()}`;
      let shiftedHour = this.hexAdd(hour, this.baseHour);
      let shiftedMinute = this.hexAdd(minute, this.baseMinute);
      let shiftedSecond = this.hexAdd(second, this.baseSecond);

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

      if (shiftedHour.length === 1) {
        shiftedHour = `0${shiftedHour}`;
      }

      if (shiftedMinute.length === 1) {
        shiftedMinute = `0${shiftedMinute}`;
      }

      if (shiftedSecond.length === 1) {
        shiftedSecond = `0${shiftedSecond}`;
      }
      
      this.hexTime = `#${hour}${minute}${second}`;
      this.hexColor = `#${shiftedHour}${shiftedMinute}${shiftedSecond}`;

      /* return {
        displayTime: `#${hour}${minute}${second}`,
        colorCode: `#${shiftedHour}${shiftedMinute}${shiftedSecond}`
      }; */
    },
    hexAdd(hex1, hex2) {
      let intSum = parseInt(hex1, 16) + parseInt(hex2, 16);
      // Color codes only go up to values of 255
      if (intSum > 255) {
        intSum = 255;
      }

      return Number(intSum).toString(16);
    },
  },
  beforeMount() {
    this.getHexTime();
  },
  mounted() {
    setInterval(() => {
      this.getHexTime();
    }, 1000);
  },
};
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