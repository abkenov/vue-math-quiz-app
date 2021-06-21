<template>
  <button 
		v-for="(operatorName, operator) in operators" 
		:key="operatorName"
		@click="$emit('changeOperator', operator)"
	>
		{{ operatorName }}
		<br>
		{{ operator }}
  </button>
</template>

<script>
export default {
  data() {
    return {
      operators: {
				'+': 'Addition',
				'-': 'Subtraction',
				'/': 'Division',
				'*': 'Multiplication'},
    }
  },

	emits: ['changeOperator'],
}
</script>

<style>

</style>