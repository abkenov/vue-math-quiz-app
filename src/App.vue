<template>
  <h1 class="main-title">
    Math Quiz App
  </h1>
  <Quiz 
    v-if="operator !== null" 
    :operator="operator"
    @nullifyOperator="nullifyOperator"
  />
  <OperatorSelector 
    v-else-if="operator === null" 
    @changeOperator="changeOperator" 
  />
</template>

<script>
import OperatorSelector from './components/OperatorSelector.vue'
import Quiz from './components/Quiz.vue';

export default {
  name: 'App',
  data() {
    return {
      operator: null,
    }
  },
  
  methods: {
    changeOperator(operator) {
      this.operator = operator;
    },

    nullifyOperator() {
      this.operator = null;
    }
  },

  components: {
    OperatorSelector,
    Quiz
  }
}
</script>

<style>


</style>