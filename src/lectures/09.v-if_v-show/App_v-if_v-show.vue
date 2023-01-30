<template>
	<div>
    <h2 v-if="visible">v-if</h2>
    <h2 v-else>false로 바뀜</h2>
    <button v-on:click="visible = !visible">toggle</button>
    <hr />
    <button v-on:click="type = 'a'">a</button>
    <button v-on:click="type = 'b'">b</button>
    <button v-on:click="type = 'c'">c</button>
    <button v-on:click="type = 'd'">d</button>
    <h2 v-if="type === 'a'">a입니다.</h2>
    <h2 v-else-if="type === 'b'">b입니다.</h2>
    <h2 v-else-if="type === 'c'">c입니다.</h2>
    <h2 v-else>a,b,c가 아닙니다.</h2>
    <template v-if="type === 'a'">
      <h1>title</h1>
    </template>
    <hr />
<!--    display: none   -->
    <h2 v-show="show">v-show</h2>
    <button v-on:click="show = !show">show toggle</button>
  </div>
</template>

<script>
import {ref} from "vue";

// v-if는 전환 비용이 높은 반면, v-show는 초기 렌더링 비용이 높다.
// 무언가를 자주 전환해야 한다면 v-show를 사용하는게 좋고, 런타임 시 조건이 변경되지 않는다면 v-if를 사용하는게 더 낫다.
export default {
	setup() {
    const visible = ref(true)
    const show = ref(true)
    const type = ref("a")
	  return {visible, show, type}
	}
}
</script>

<style lang="scss" scoped></style>
