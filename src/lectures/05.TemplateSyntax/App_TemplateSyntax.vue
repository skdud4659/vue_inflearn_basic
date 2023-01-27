<template>
	<div>
		<h2>텍스트 보간법</h2>
		<p>반응형 상태: {{ message }}</p>
		<button v-on:click="handleClickText">텍스트 변경하기</button>
		<p v-once>일회성 보간: {{ message }}</p>
		<hr />
		<h2>v-html : 실제 HTML을 출력하는 디렉티브</h2>
		<p>{{ rawHtml }}</p>
		<p v-html="rawHtml"></p>
		<hr />
		<h2>v-bind : 속성 바인딩</h2>
		<div v-bind:title="dynamicTitle">마우스를 올려보세요</div>
		<!--    :만 작성해도 가능-->
		<!--		<div :title="dynamicTitle">단축 속성 :: 마우스를 올려보세요</div>-->
		<!--    다중속성 가능-->
		<input v-bind="attrs" />
		<hr />
		<h2>javascript</h2>
		{{ message.split('').reverse().join('') }}
	</div>
</template>

<script>
import { ref } from 'vue'

export default {
	// compositionAPI 사용을 위한 진입점 역할을 함 > 컴포넌트 인스턴스가 생성되기 전에 실행됨.
	// setup(props, context)
	setup() {
		const message = ref('hello')
		const rawHtml = ref('<strong>안녕하세요</strong>')
		const dynamicTitle = ref('안녕하세요!!!')
		const attrs = ref({
			type: 'password',
			value: '12345678',
			disable: true,
		})
		const handleClickText = () => {
			message.value = 'change!!'
		}
		return {
			message,
			rawHtml,
			dynamicTitle,
			attrs,
			handleClickText,
		}
	},
}
</script>

<style lang="scss" scoped></style>
