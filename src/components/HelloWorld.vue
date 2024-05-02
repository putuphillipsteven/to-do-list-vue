<script setup>
defineProps({
	msg: String,
	rawHtml: String,
});
</script>

<template>
	<h1>{{ msg }}</h1>
	<p>Using text interpolation: <span class="text-red-500">This should be red.</span></p>
	<p>Using v-html directive: <span v-html="rawHtml" class="text-red-500"></span></p>
</template>
