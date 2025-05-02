<script setup>
const { locales, setLocale } = useI18n()

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

	<div>
		<button
			v-for="locale in locales"
			@click="setLocale(locale.code)"
			:key="locale.name"
		>
			{{ locale.name }}
		</button>
		<h1>{{ $t("welcome") }}</h1>
		<div>{{ $t("hello") }}</div>
		<div>{{ $t("form.name") }}</div>
		<div>{{ $t("form.email") }}</div>
	</div>
</template>
