<script>
import ColorPickerGame from './components/ColorPickerGame.vue'
import Recap_01_02_2023 from './components/Recap_01_02_2023.vue'

export default {
  components: { ColorPickerGame, Recap_01_02_2023 },
  data() {
    return {
      currentLesson: 'color-picker-game',
    }
  },
}
</script>

<template>
  <div class="container">
    <ColorPickerGame v-if="currentLesson === 'color-picker-game'" />
    <Recap_01_02_2023 v-else />
  </div>
</template>

<style scoped>
.container {
  background: red;
  padding: 5rem;
  background: teal;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  border-radius: 10px;
  margin: 0 auto;
  width: auto;
}
</style>
