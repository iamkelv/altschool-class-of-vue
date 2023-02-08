<template>
  <div>
    <h1>Color Picker Game</h1>
    <div class="body" :style="{ 'background-color': background }">
      <div v-if="res === 'Pick a color...'">{{ res }}</div>
      <div v-else>{{ res }}😊</div>
    </div>
    <div class="buttons">
      <button v-for="color in colors" :key="color" @click="match(color)">
        {{ color }}
      </button>
    </div>
  </div>
</template>

<script>
import { matchColor } from '../composables/useColorPicker'
import { ref } from 'vue'
export default {
  setup() {
    const colors = ['green', 'red', 'blue', 'purple']
    let res = ref('Pick a color...')
    let background = ref('')
    const match = (color) => {
      let { message, messageColor } = matchColor(color, colors)
      background.value = messageColor
      res.value = message
    }
    return { res, match, colors, background }
  },
}
</script>

<style scoped>
.body {
  display: flex;
  width: 400px;
  justify-content: center;
  align-items: center;
  min-height: 60px;
  color: white;
  background-color: grey;
  border-radius: 20px;
  margin: 10px;
}
h1 {
  text-align: center;
  color: white;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.2rem;
}
button {
  background: white;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  border-radius: 10px;
  padding: 1rem;
  border: none;
  font-weight: bold;
  font-family: lato;
  text-transform: capitalize;
  cursor: pointer;
}
</style>
