<template>
	<div>
    <h2>v-text : string</h2>
    <span v-text="text"/>
    <hr />
    <h2>v-html : node</h2>
    <span v-html="html"/>
    <hr />
    <h2>v-cloak : 렌더링되면 사라짐</h2>
    <span v-cloak>{{ cloak }}</span>
    <hr />
    <h2>v-memo : 배열 안에 있는 요소가 변경되었을 때에만 업데이트</h2>
    <div v-memo="[subscribers]">
      <p>subscribers: {{ subscribers }}</p>
      <p>views: {{ views }}</p>
      <p>likes: {{ likes }}</p>
      <button @click="subscribers++">subscribers</button>
      <button @click="views++">views</button>
      <button @click="likes++">likes</button>
    </div>
  </div>
</template>

<script>
import {ref} from "vue";

export default {
	setup() {
    const text = "hello"
    const html = ref("<strong>hello!!!!</strong>")
    const cloak = "loading..."

    const subscribers = ref(4000)
    const views = ref(400)
    const likes = ref(20)
	  return {
      text,
      html,
      cloak,
      subscribers,
      views,
      likes
    }
	}
}
</script>

<style lang="css" scoped>
  [v-cloak] {
    display: none;
  }
</style>
