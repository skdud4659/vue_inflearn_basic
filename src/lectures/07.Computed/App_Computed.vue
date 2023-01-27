<template>
	<div>
		<h2>일반 :: 코드 복잡성이 높아짐</h2>
		<p>{{ teacher.name }}</p>
		<p>{{ teacher.lectures.length > 0 ? '있음🌟' : '없음🥲' }}</p>
		<hr />
		<h2>computed :: 코드가 간단해짐</h2>
		<p>{{ teacher.name }}</p>
		<p>{{ hasLecture }}</p>
		<p>{{ existLecture() }}</p>
		<hr />
		<h2>computed :: get, set</h2>
		<p>{{ fullName }}</p>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue'

export default {
	setup() {
		const teacher = reactive({
			name: 'teacher',
			lectures: ['HTML/CSS', 'Javascript', 'Vue 3'],
		})
		// computed : 계산된 값이 캐싱되어 일반 메소드보다 리소스를 덜 사용함. 내부 반응형 데이터가 변경될 때만 적용.
		// getter 전용
		const hasLecture = computed(() => {
			console.log('computed')
			return teacher.lectures.length > 0 ? '있음🌟' : '없음🥲'
		})
		const existLecture = () => {
			console.log('method')
			return teacher.lectures.length > 0 ? '있음🌟' : '없음🥲'
		}
		const firstName = ref('홍')
		const lastName = ref('길동')
		const fullName = computed({
			get() {
				return firstName.value + ' ' + lastName.value
			},
			set(value) {
				const [first, last] = value.split(' ')
				firstName.value = first
				lastName.value = last
			},
		})
		fullName.value = '김 가을'
		return {
			teacher,
			hasLecture,
			existLecture,
			fullName,
		}
	},
}
</script>

<style lang="scss" scoped></style>
