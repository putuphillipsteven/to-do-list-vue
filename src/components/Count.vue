<script setup>
import { defineProps, ref } from 'vue';

const props = defineProps({
	userName: String,
});

const childData = ref('Test');

// Define methods
const updateChildData = () => {
	childData.value = 'Updated Test';
};
</script>

<template>
	<div>
		<h1>Hello {{ userName }}</h1>
		<p>Child Data: {{ childData }}</p>
		<button @click="updateChildData">Update Child Data</button>
	</div>
</template>
