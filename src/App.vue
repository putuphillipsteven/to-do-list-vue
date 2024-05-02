<script>
import HelloWorld from './components/HelloWorld.vue';
import Count from './components/Count.vue';
import { nextTick } from 'vue';
export default {
	data() {
		return {
			count: 0,
		};
	},
	methods: {
		async increment() {
			this.count++;
			await nextTick();
		},
		async decrement() {
			this.count--;
			await nextTick();
		},
	},
	mounted() {
		this.increment();
	},
	computed: {
		isEvenNumber() {
			return this.count % 2 === 0 ? 'Even Number' : 'Odd Number';
		},
	},
	components: {
		HelloWorld,
		Count,
	},
};
</script>

<template>
	<div class="flex flex-col gap-y-4">
		<HelloWorld msg="Hello World" rawHtml="This should be red" />
		<hr />
		<Count userName="Putu" />
		<p class="text-2xl">{{ count }}</p>
		<p>{{ isEvenNumber }}</p>
		<p class="text-red-500">Why show 1? because of the mounted is default incrementing</p>
		<div class="flex justify-between">
			<button @click="increment">Increment</button>
			<button @click="decrement">Decrement</button>
		</div>
	</div>
</template>

<style scoped>
.logo {
	height: 6em;
	padding: 1.5em;
	will-change: filter;
	transition: filter 300ms;
}
.logo:hover {
	filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
	filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
