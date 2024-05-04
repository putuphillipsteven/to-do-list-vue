<template>
	<div class="container">
		<div class="task">
			<!-- title -->
			<div class="title">
				<h1>To Do List</h1>
			</div>
			<!-- form -->
			<div class="form flex items-center gap-x-4">
				<input
					type="text"
					placeholder="New Task"
					v-model="newTask"
					@keyup.enter="addTask"
					class="px-2 py-1 rounded-md"
				/>
				<button @click="addTask" class="px-2 py-1">Add Tasks</button>
				<div class="w-10 h-10 border border-black"></div>
				<v-icon name="hi-plus-sm" />
				<p>Test</p>
			</div>
			<!-- task lists -->
			<div class="taskItems">
				<ul>
					<task-item
						v-bind:task="task"
						v-for="(task, index) in tasks"
						:key="task.id"
						@remove="removeTask(index)"
						@complete="completeTask(task)"
					></task-item>
				</ul>
			</div>
			<!-- buttons -->
			<div class="clearBtns">
				<button @click="clearCompleted">Clear completed</button>
				<button @click="clearAll">Clear all</button>
			</div>
			<!-- pending task -->
			<div class="pendingTasks">
				<span>Pending Tasks: {{ incomplete }}</span>
			</div>
		</div>
	</div>
</template>

<script>
import TaskItem from './TasksItems.vue';
export default {
	name: 'Task',
	// Register props
	props: ['tasks'],
	// Register Component
	components: {
		TaskItem,
	},
	data() {
		return {
			newTask: '',
		};
	},
	computed: {
		incomplete() {
			return this.tasks.filter(this.inProgress).length;
		},
	},
	methods: {
		addTask() {
			if (this.newTask) {
				this.tasks.push({
					title: this.newTask,
					completed: false,
				});
				this.newTask = '';
			}
		},
		inProgress(task) {
			return !this.isCompleted(task);
		},
		isCompleted(task) {
			return task.completed;
		},
		clearCompleted() {
			this.tasks = this.tasks.filter(this.inProgress);
		},
		clearAll() {
			this.tasks = [];
		},
		completeTask(task) {
			task.completed = !task.completed;
		},
		removeTask(index) {
			this.tasks.splice(index, 1);
		},
	},
};
</script>
