<template>
	<div class="task-list">
		<template v-if="tasks.length">
			<Task v-for="(task, i) in tasks" :key="task.name" :task="task"
			@taskDeleted="$emit('taskDeleted', i)"
			@taskStateChanged="$emit('taskStateChanged', i)" />
		</template>
		<p v-else class="no-task">Nenhuma tarefa foi cadastrada</p>
	</div>
</template>

<script>
	import Task from '@/components/Task.vue'

	export default {
		components: {
			Task,
		},
		props: {
			tasks: {
				type: Array,
				required: true
			}
		}
	}
</script>

<style>
	.task-list {
		display: block;
		justify-content: center;
	}

	.no-task {
		color: var(--color-text-disable);
		font-size: 2.2rem;
	}
</style>
