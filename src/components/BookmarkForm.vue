<template>
  <div class="form">
    <input v-model="title" placeholder="標題（可選）" />
    <input v-model="url" placeholder="網址" />
    <button @click="submit">新增</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const emit = defineEmits(['add-bookmark']);

const title = ref('');
const url = ref('');

const submit = () => {
  if (!url.value.trim()) return alert('請輸入網址');
  emit('add-bookmark', {
    title: title.value || url.value,
    url: url.value,
  });
  title.value = '';
  url.value = '';
};
</script>
