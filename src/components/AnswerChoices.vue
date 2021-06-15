<template>
  <button 
		v-for="(choice, idx) in choices" 
		:key="idx" 
		@click="handleChoice(choice), $emit('startQuiz'), generateAnswers()"
	>
		{{ choice }}
	</button>
	<h4 v-if="isCorrect">Answer is correct</h4>
	<h3>Streak of correct answers: {{ correctStreak }}</h3>
</template>

<script>
export default {
  props: ['leftOperand', 'rightOperand', 'operator'],
  data() {
    return {
      choices: [],
			correctAnswer: null,
			isCorrect: false,
			correctStreak: 0,
    }
  },
  methods: {
		shuffle(array) {
			for (let i = array.length - 1; i > 0; i--) {
				let j = Math.floor(Math.random() * (i + 1));
				[array[i], array[j]] = [array[j], array[i]];
			}
		},

    generateAnswers() {
			this.choices.length = 0

			const methods = {
				'+': (a, b) => a + b,
				'-': (a, b) => a - b,
				'/': (a, b) => a / b,
				'*': (a, b) => a * b,
			}

			const usedMethod = methods[this.operator]

			while(this.choices.length < 4) {
				const candidate = usedMethod(
					Math.floor(Math.random() * 5),
					Math.floor(Math.random() * 5)
				)

				if(!this.choices.includes(candidate)) {
					this.choices.push(candidate)
				}
			}

			this.correctAnswer = usedMethod(this.leftOperand, this.rightOperand)
			this.choices.push(this.correctAnswer)

			this.shuffle(this.choices)
    },

		handleChoice(choice) {
			this.isCorrect = choice === this.correctAnswer ? true : false
			this.isCorrect ? this.correctStreak++ : this.correctStreak = 0
		}
  },
	mounted() {
		this.choices.length = 0
		this.generateAnswers()
	},
	updated() {
		this.choices.length = 0
		this.generateAnswers()
	},
	emits: ['startQuiz']
}
</script>

<style>

</style>