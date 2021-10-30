<template>
	<div id="app">
		<h1>Gerenciamento de Tarefas</h1>
		<NewTask @taskAdded="addTask" />
		<h2>Tarefas</h2>
		<TaskList  :tasks="tasks" />
	</div>
</template>

<script>
	import NewTask from './components/NewTask'
	import TaskList from './components/TaskList.vue'

	export default {
		name: 'App',
		components: {
			NewTask,
			TaskList,
		},
		data() {
			return {
				tasks: [
					{ name: 'Lavar a louça', pending: false },
					{ name: 'Comprar blusa', pending: true },
				]
			}
		},
		methods: {
			addTask(task) {
				const sameName = t => t.name === task.name
				const reallyNew = this.tasks.filter(sameName).length == 0

				reallyNew && this.tasks.push({
					name: task.name,
					pending: task.pending || true
				})
			}
		}
	}
</script>

<style>

	:root {
		--bg-white: #FAFCFF;
		--bg-gray: #F0F4FA;
		--color-text-disable: #a8b5c4;
		--color-text-primary: #0E2847;
		--color-text-second: #081627;

		font-family: 'Poppins', sans-serif;
		font-size: 10px;
	}

	body {
		background-color: var(--bg-white);
		color: var(--color-text-second);
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		font-weight: 600;
		font-size: 4.8rem;
	}

	#app h2 {
		font-weight: 500;
		font-size: 3.2rem;
	}

</style>
