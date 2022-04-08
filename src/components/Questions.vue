<script>
export default {
	name: "Questions",
	data() {
		return {
			elements: [
				{
					question: "Jakiego języka skryptowego używa silnik Unity?",
					right: 2,
					answers: [
						"JavaScript",
						"C++",
						"C#",
						"Lua"
					]
				},
				{
					question: "Co jest aktualnie najstabilniejszym i polecanym przez Unity UI",
					right: 2,
					answers: [
						"IMGUI",
						"Unity UI",
						"Unity UI + TextMeshPro",
						"UI Elements"
					]
				},
				{
					question: "Jaki stabilny networking jest aktualnie najbardziej zbliżony do HLAPI",
					right: 1,    
					answers: [
						"MLAPI",
						"Mirror",
						"PUN(Phtoton Networking)",
						"Vivox"
					]
				},
				{
					question: "Jakiej platformy nie wspiera Unity 2019.X",
					right: 1,    
					answers: [
						"PS5",
						"XBOX Seriex",
						"PowerPC",
						"ARM"
					]
				}
			],
			correctNumber: 0,
			answered: [],
		};
	},
	methods: {
		check: function(index, _index) {
			if (this.answered[index] == true) {
				return;
			}
			this.answered[index] = true;
			
			if (_index == this.elements[index].right) {
				this.correctNumber++;
			}
		}
	}
};
</script>

<template>
	<nav>
		<h2>Poprawne odpowiedzi: {{ correctNumber }}/{{elements.length}}</h2>
	</nav>
	<div class="separator"></div>
	<section v-for="(element, index) in elements" :key="element.index">
		<h2>{{element.question}}</h2>
		<div class="buttons">
			<button v-for="(answer, _index) in element.answers" :key="answer._index" @click="check(index, _index)">{{answer}}</button>
		</div>
	</section>

	
</template>

<style lang="scss">
h2 {
	font-size: 2rem;
}
nav {
	text-align: center;
	padding: .25rem 0;
	position: fixed;
	width: 100%;
	background-color: #333;
}

section {
	max-width: 35rem;
	margin-inline: auto;
	padding-bottom: 5rem;
	display: flex;
	flex-direction: column;
	align-items: center;
	text-align: center;
}
.separator {
	padding-top: 6rem;
	
}
.buttons {
	width: 100%;
	display: grid;
	gap: 20px;
	grid-template-columns: 1fr 1fr;
	
	button {
		min-height: 5rem;
		background-color: #3498db;
		border: .25rem dashed #2980b9;
		border-radius: 10px;
		font-size: 1.25rem;

		user-select: none;

		cursor: pointer;
		transition-duration: 200ms;
		&:hover {
			background-color: #e67e22;
			border-color: #d35400;
			border-width: 0.4rem;
		}
	}
}
.test {
	color: red;
}
.correct {
	background-color: #2ecc71;
	border: .25rem dashed #27ae60;
	cursor: not-allowed;
}
</style>
