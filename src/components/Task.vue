<template>
	<div class="task" :class="stateClass">
		<p>{{ task.name }}</p>
	</div>
</template>

<script>
	export default {
		props: {
			task: {
				type: Object,
				required: true
			}
		},
		computed: {
			stateClass() {
				return {
					pending: this.task.pending,
					done: !this.task.pending
				}
			}
		}
	}
</script>

<style>
	.task {
		box-sizing: border-box;
		width: 45rem;
		height: 10rem;
		padding: 1.6rem;
		font-size: 1.8rem;
		font-weight: 500;
		background: var(--bg-gray);
		border-radius: .8rem;
		margin-bottom: 2.4rem;
		cursor: pointer;
		user-select: none;
	}

	.task:last-child{
		margin: 0;
	}

	.task p {
		margin: 0;
	}

	.pending {
		border-left: .8rem solid #c53228;

	}

	.done {
		border-left: .8rem solid #27c024;
		text-decoration: line-through;
		color: var(--color-text-disable)
	}
</style>
