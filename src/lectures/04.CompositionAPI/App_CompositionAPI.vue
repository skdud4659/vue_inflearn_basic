<template>
	<div>
		<h2>반응형 메세지</h2>
		<p>{{ reactiveMessage }}</p>
		<button v-on:click="addReactiveMessage">add reactive message</button>
		<h2>일반 메세지</h2>
		<p>{{ normalMessage }}</p>
		<button v-on:click="addNormalMessage">add normal message</button>
	</div>
</template>

<script>
import { onBeforeMount, onMounted, ref } from 'vue'

export default {
	setup() {
		console.log('setup')
		// 반응형 API
		const reactiveMessage = ref('hello reactive message')
		let normalMessage = 'normal message'

		const addReactiveMessage = () => {
			reactiveMessage.value = reactiveMessage.value + '!'
		}
		const addNormalMessage = () => {
			normalMessage = normalMessage + '!'
		}

		// Lifecycle
		onBeforeMount(() => {
			console.log('onBeforeMount')
		})
		onMounted(() => {
			console.log('onMounted')
		})

		return {
			reactiveMessage,
			normalMessage,
			addReactiveMessage,
			addNormalMessage,
		}
	},
}
</script>

<style lang="scss" scoped></style>
