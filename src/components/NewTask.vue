<template>
	<div class="new-task">
		<input v-model="name" @keydown.enter="add" type="text"
			class="form-element" placeholder="Nova tarefa">
		<button class="form-element" @click="add">Adicionar</button>
	</div>
</template>

<script>
export default {
	data() {
		return {
			name: ''
		}
	},
	methods: {
		add() {
			this.$emit('taskAdded', { name: this.name })
			this.name = ''
		}
	}
}
</script>

<style>
	.new-task {
		margin: 35px 0;
		width: 45rem;
		display: flex;
		justify-content: space-between;
	}

	.form-element {
		outline: none;
		font-size: 2.4rem;
		border: 2px solid var(--bg-gray);
		border-radius: .8rem;
		padding: 1.6rem
	}

	input.form-element {
		width: 25rem;
		background: var(--bg-gray);
		transition: border 300ms ease-in-out;
	}

	input.form-element:focus {
		border: 2px solid var(--color-text-second);
	}

	button.form-element {
		background: var(--bg-darkblue);
		color: #fff;
		cursor: point;
		transition: background 300ms ease-in-out;
	}

	button.form-element:hover {
		background: var(--color-text-second);
	}
</style>
