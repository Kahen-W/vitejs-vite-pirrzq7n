<template>
<ul class="list">
  <li v-for="(bookmark, index) in bookmarks" :key="index">
    <a :href="bookmark.url" target="_blank">{{ bookmark.title }}</a>
    <button @click="$emit('delete-bookmark', index)">刪除</button>
  </li>
</ul>
</template>

<script setup>
defineProps({
bookmarks: Array
})
</script>
