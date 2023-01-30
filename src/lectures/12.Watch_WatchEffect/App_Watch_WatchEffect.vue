<template>
  <div>{{ immediate }}</div>
  <div>{{ reverseMsg }}</div>
  <div>
    <form @submit.prevent="save(title, content)">
      <input v-model.lazy="title" placeholder="title" type="text"/>
      <textarea v-model.lazy="content" placeholder="content"/>
      <hr />
      <button >저장</button>
    </form>
  </div>
</template>

<script>
import {ref, watch, watchEffect} from "vue";

export default {
	setup() {
    const msg = ref("")
    const immediate = ref("hello vue")
    const reverseMsg = ref("")
    const title = ref("")
    const content = ref("")
    // 첫번째 매개변수의 값이 변함을 감지할 때 함수 호출. 명시적으로 관찰
    watch(msg, (newValue, oldValue) => {
      console.log({newValue, oldValue})
    })
    const reverseFunc = (newValue) => {
      reverseMsg.value = newValue.split('').reverse().join('')
    }
    // 렌더링 즉시 실행
    watch(immediate, (newValue) => reverseFunc(newValue), {
      immediate: true
    })
    const save = (title, content) => {
      console.log(`저장 완료 ${title}, ${content}`)
    }
    // watchEffect : 콜백 함수 내부의 값이 변경될 때 함수 호출. 기본적으로 최초 즉시 실행.
    watchEffect(() => {
      save(title.value, content.value)
    })
	  return {
      msg,
      immediate,
      reverseMsg,
      title,
      content,
      save
    }
	}
}
</script>

<style lang="scss" scoped></style>
