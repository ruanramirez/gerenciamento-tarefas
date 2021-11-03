<template>
	<div class="tasks-progress">
		<span class="progress-value">{{ progress }}%</span>
		<div class="progress-bar" :style="{width: progress + '%'}"></div>
	</div>
</template>

<script>
	export default {
		props: {
			progress: {
				type: Number,
				default: 0
			}
		}
	}
</script>

<style>
	.tasks-progress {
		position: relative;
		width: 30%;
		border: 1px solid var(--bg-gray);
		border-radius: .8rem;
		color: var(--bg-darkblue);
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.progress-bar {
		position: absolute;
		border-radius: .8rem;
		height: 100%;
		background-color: #4CAF50;
		align-self: flex-start;
	}

	.progress-value {
		z-index: 9999;
		font-size: 1.6rem;
	}

</style>
