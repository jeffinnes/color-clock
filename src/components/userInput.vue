<template>
<div id="userInput">
  <p>The current base color code is {{ baseColor }}.</p>
  <p>You can set a different base color below and see how it changes the current time's color.</p>
  <div class="color-selections">
    <div class="base-color-selector" :style="{backgroundColor: base1, color: '#ffffff'}" @click="updatePreview(base1)">{{ base1 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base2, color: '#ffffff'}" @click="updatePreview(base2)">{{ base2 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base3}" @click="updatePreview(base3)">{{ base3 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base4}" @click="updatePreview(base4)">{{ base4 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base5, color: '#ffffff'}" @click="updatePreview(base5)">{{ base5 }}</div>
    <div class="base-color-selector" :style="{backgroundColor: base6, color: '#ffffff'}" @click="updatePreview(base6)">{{ base6 }}</div>
  </div>
</div>
</template>

<script setup>
  import { ref } from 'vue';

  const emit = defineEmits(['update-base-color']);

  const baseColor = ref("#000000");
  const base1 = "#a60000";
  const base2 = "#a600a6";
  const base3 = "#00a600";
  const base4 = "#00a6a6";
  const base5 = "#0000a6";
  const base6 = "#000000";

  function updatePreview(newBaseColor) {
    baseColor.value = newBaseColor;
    emit('update-base-color', newBaseColor);
  };
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