<template>
<div id="userInput">
  <p>The current base color code is {{ baseColor }}. You can set a different base color and see how it changes the day's colors below.</p>
  <div class="color-selections">
    <div class="base-color-selector" :style="{backgroundColor: base1}" @click="updatePreview(base1)">{{ base1 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base2}" @click="updatePreview(base2)">{{ base2 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base3}" @click="updatePreview(base3)">{{ base3 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base4}" @click="updatePreview(base4)">{{ base4 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base5, color: '#fff'}" @click="updatePreview(base5)">{{ base5 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base6, color: '#fff'}" @click="updatePreview(base6)">{{ base6 }}</div>
  </div>
  <div id="colorPreview">The color preview will go here</div>
</div>
</template>

<script>
export default {
  name: 'userInput',
  data () {
    return {
      baseColor: "#000000",
      base1: "#a60000",
      base2: "#a600a6",
      base3: "#00a600",
      base4: "#00a6a6",
      base5: "#0000a6",
      base6: "#000000",
    }
  },
  methods: {
    updatePreview(newBaseColor) {
      this.baseColor = newBaseColor;
      this.$emit('update-base-color', newBaseColor);
    },
  }
}
</script>

<style scoped>
#userInput {
  grid-column: span 12;
  font-size: 2.5rem;
}

div.color-selections {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

div.base-color-selector {
  padding: .5rem 1rem;
  margin: .5rem;
  border: 1px solid #000000;
  font-weight: bold;
}

</style>