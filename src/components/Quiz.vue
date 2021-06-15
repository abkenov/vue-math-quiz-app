<template>
  <h4 v-if="isStarted">{{ leftOperand }} {{ operator }} {{ rightOperand }}</h4>
  <button v-if="!isStarted" @click="startQuiz">Start</button>
  <answer-choices 
    v-if="isStarted" 
    :leftOperand="leftOperand" 
    :rightOperand="rightOperand" 
    :operator="operator"
    @startQuiz="startQuiz"
  />
  <br>
  <button @click="$emit('nullifyOperator')">Back</button>
</template>

<script>
import AnswerChoices from './AnswerChoices.vue'

export default {
  components: { AnswerChoices },
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
        this.leftOperand = Math.floor(Math.random() * 20) + 1
        this.rightOperand = Math.floor(Math.random() * 20) + 1
        this.isStarted = true;
    }
  }
}
</script>

<style>

</style>