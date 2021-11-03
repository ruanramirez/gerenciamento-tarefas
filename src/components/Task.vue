<template>
	<div
		@click="$emit('taskStateChanged', task)"
		class="task" :class="stateClass">
		<p>{{ task.name }}</p>
		<span @click.stop="$emit('taskDeleted', task)" class="close"><img class="svg" src="../assets/times-solid.svg" alt="close"></span>
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
		position: relative;
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

	.pending .close {
		background: #c53228dd;
		color: var(--bg-white);
		transition: background 200ms ease-in-out;
	}

	.pending .close:hover{
		background: #c53228;
	}

	.done .close {
		background: #1aac18dd;
		color: var(--bg-white);
		transition: background 200ms ease-in-out;
	}

	.done .close:hover{
		background: #1aac18;
	}

	.close {
		position: absolute;
		right: 1rem;
		top: 1rem;
		width: 2rem;
		height: 2rem;
		border-radius: 50%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.close .svg {
		width: 1rem;

	}
</style>
