<template>
	<div id="app">
		<h1>Gerenciamento de Tarefas</h1>
		<TaskProgress :progress="progress"/>
		<NewTask @taskAdded="addTask" />
		<h2>Tarefas</h2>
		<TaskList  :tasks="tasks"
			@taskDeleted="deletedTask"
			@taskStateChanged="toggleTaskState"/>
	</div>
</template>

<script>
	import TaskProgress from './components/TaskProgress.vue'
	import NewTask from './components/NewTask.vue'
	import TaskList from './components/TaskList.vue'

	export default {
		name: 'App',
		components: {
			NewTask,
			TaskList,
			TaskProgress,
		},
		data() {
			return {
				tasks: []
			}
		},
		computed: {
			progress() {
				const total = this.tasks.length
				const done = this.tasks.filter(t => !t.pending).length

				return Math.round(done / total * 100) || 0
			}
		},
		watch: {
			tasks: {
				deep: true,
				handler() {
					localStorage.setItem('tasks', JSON.stringify(this.tasks))
				}
			}
		},
		methods: {
			addTask(task) {
				const sameName = t => t.name === task.name
				const reallyNew = this.tasks.filter(sameName).length == 0

				if(reallyNew){
					this.tasks.push({
						name: task.name,
						pending: task.pending || true
					})
				} else {
					alert('Ação inválida.')
				}
			},
			deletedTask(i) {
				this.tasks.splice(i, 1)
			},
			toggleTaskState(i) {
				this.tasks[i].pending = !this.tasks[i].pending
			}
		},
		created() {
			const json = localStorage.getItem('tasks')
			const array = JSON.parse(json)

			this.tasks = Array.isArray(array) ? array : []
		}
	}
</script>

<style>

	:root {
		--bg-white: #FAFCFF;
		--bg-gray: #F0F4FA;
		--bg-darkblue: #182e4baa;
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
