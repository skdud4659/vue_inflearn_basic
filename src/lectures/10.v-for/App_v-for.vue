<template>
	<div>
    <ul>
<!--      <template v-for="(item, index) in items" :key="item.id">-->
<!--        <li v-if="item.id % 2 === 0">-->
<!--          id: {{ item.id }} 인덱스: {{ index }}, 메세지: {{ item.message }}-->
<!--        </li>-->
<!--      </template>-->
      <li v-for="(item, index) in evenItems" :key="item.id">
        id: {{ item.id }} 인덱스: {{ index }}, 메세지: {{ item.message }}
      </li>
    </ul>
    <h2> v-for 객체 : 객체 순서대로 출력됨 </h2>
    <ul>
      <li v-for="(item, key, index) in object" :key="key">
        id: {{ index + 1 }}, key: {{ key }}, value: {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
import {computed, reactive} from "vue";

export default {
	setup() {
    const items = reactive([
      { id: 1, message: 'java'},
      { id: 2, message: 'html'},
      { id: 3, message: 'css'},
      { id: 4, message: 'javascript'},
    ])
    const evenItems = computed(() => items.filter((item) => item.id % 2 === 0))
    const object = reactive({
      title: 'title',
      author: 'author',
      publishedAt: '2016-04-10'
    })
	  return {
      items,
      evenItems,
      object
    }
	}
}
</script>

<style lang="scss" scoped></style>
