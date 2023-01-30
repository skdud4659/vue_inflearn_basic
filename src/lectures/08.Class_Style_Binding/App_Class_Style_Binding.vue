<template>
	<div>
    <h2> class </h2>
<!--    class 공존 가능-->
<!-- class 객체 내용이 너무 많다면 별도로 객체를 생성하여 관리-->
    <div class="text" :class="classObject">
<!--      <div class="text" :class="{ active: isActive, 'has-error': isError }">-->

      텍스트입니다.
    </div>
    <button v-on:click="toggle">toggle</button>
    <button v-on:click="toggleError">toggleError</button>
  </div>
  <div>
    <h2> style </h2>
    <p :style="styleObject">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
    <button v-on:click="fontSize--">-</button>
    <button v-on:click="fontSize++">+</button>
  </div>
</template>

<script>
import {computed, reactive, ref} from "vue";

export default {
	setup() {
    // class
    const isActive = ref(true)
    const isError = ref(false)
    const classObject = reactive({ active: isActive, 'has-error': isError })
    // style
    const fontSize = ref(13)
    const styleObject = computed(() => {
      return {
        color: 'red',
        fontSize: fontSize.value + 'px'
      }
    })
    console.log(fontSize)

    const toggle = () => {
      isActive.value = !isActive.value
    }
    const toggleError = () => {
      isError.value = !isError.value
    }
		return {
      isActive,
      isError,
      classObject,
      fontSize,
      styleObject,
      toggle,
      toggleError
    }
	},
}
</script>

<style lang="css" scoped>
  .active {
    font-weight: 700;
  }
  .has-error {
    color: red;
  }
</style>
