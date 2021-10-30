<template>
	<div class="task-list">
		<template v-if="tasks.length">
			<Task v-for="task in tasks" :key="task.name" :task="task" />
		</template>
		<p v-else class="no-task">Sua vida está em dia</p>
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
