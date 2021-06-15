<template>
  <h4 v-if="isStarted">{{ operator }}</h4>
  <button @click="startQuiz">Start</button>
  <button @click="$emit('nullifyOperator')">Back</button>
</template>

<script>
export default {
  props: ['operator'],
  emits: ['nullifyOperator'],
  data() {
    return {
        isStarted: false,
        leftOperand: null,
        rightOperand: null,
    }
  },
  methods: {
    startQuiz() {
        this.isStarted = true;
    }
  }
}
</script>

<style>

</style>