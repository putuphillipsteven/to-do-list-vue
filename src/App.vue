<template>
	<div id="app">
		<Task :tasks="tasks"></Task>
	</div>
</template>

<script>
import Task from './components/Task.vue';
import { OhVueIcon, addIcons } from 'oh-vue-icons';
import { BiPlusLg } from 'oh-vue-icons/icons';

export default {
	name: 'App',
	// Registering component
	components: {
		Task,
	},
	data() {
		return {
			tasks: [
				{
					id: 1,
					title: 'Learn Vue JS',
					completed: true,
				},
				{
					id: 2,
					title: 'Watch netflix',
					completed: true,
				},
				{
					id: 3,
					title: 'Go shopping',
					completed: false,
				},
				{
					id: 4,
					title: 'Learn guitar',
					completed: false,
				},
				{
					id: 5,
					title: 'Send email',
					completed: false,
				},
			],
		};
	},
};
</script>
