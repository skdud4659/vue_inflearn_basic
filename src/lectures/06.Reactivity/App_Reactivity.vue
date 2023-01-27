<template>
	<div>
		<h2>reactive :: 참조 타입 반응형</h2>
		<button v-on:click="increment">Click {{ state.count }}</button>
		<button v-on:click="increment">Deep Click {{ state.deep.count }}</button>
		<hr />
		<h2>reactive :: 원시 타입 반응형 불가</h2>
		<p>{{ message }}</p>
		<button v-on:click="addMessage">Add Message</button>
		<hr />
		<h2>ref :: 원시 타입 반응형</h2>
		<p>{{ primitiveMessage }}</p>
		<button v-on:click="addPrimitiveMessage">Add Message</button>
	</div>
</template>

<script>
import { reactive, readonly, ref } from 'vue'

export default {
	setup() {
		// reactive : 객체나 배열과 같은 참조 타입을 반응형으로 만들어줌
		const state = reactive({
			count: 0,
			deep: {
				count: 0,
			},
		})
		let message = reactive('hello vue')
		// ref : 원시 타입을 반응형으로 만들어줌
		// ref 메서드는 변이가능한 객체로 리턴하기 때문에 이 객체를 참조하여 반응형이 진행.
		let primitiveMessage = ref('primitive!')

		const increment = () => {
			state.count++
			state.deep.count++
		}
		const addMessage = () => {
			message = message + '!'
		}
		const addPrimitiveMessage = () => {
			primitiveMessage.value = primitiveMessage.value + '!'
		}

		// ref -> object
		const refCount = ref(0)
		const refState = reactive({
			refCount,
		})
		console.log(refState.refCount) // 0, 원본인 count도 같이 변경됨, .value 필요없음
		// ref -> array
		const refMessage = ref('hello')
		const arr = reactive([refMessage])
		console.log(arr[0].value) // hello, .value 필요

		// readonly :: 반응형 객체의 변경 방지
		const original = reactive({
			count: 0,
		})
		const copy = readonly(original)
		original.count++
		// copy.count++ > error
		console.log({ original: original.count, copy: copy.count })

		return {
			state,
			message,
			primitiveMessage,
			increment,
			addMessage,
			addPrimitiveMessage,
		}
	},
}
</script>

<style lang="scss" scoped></style>
