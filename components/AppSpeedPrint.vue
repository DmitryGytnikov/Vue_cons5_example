<script setup>
const fact = ref("")
const typedText = ref("")

const fetchData = () => {
	fetch("https://api.api-ninjas.com/v1/quotes", {
		method: "GET",
		headers: {
			"X-Api-Key": "MaJRZbQ2E6XJoWM9vfJa0g==iwIoVBVzxFPkB5c2",
		},
	})
		.then(response => {
			response.json().then(data => {
				fact.value = data[0].quote
			})
		})
		.catch(err => {
			console.error(err)
		})
}
</script>

<template>
	<h1>Рандомная цитата</h1>
	<button @click="fetchData">Click Me!</button>
	<p>{{ fact }}</p>
</template>
