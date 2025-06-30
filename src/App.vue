<template>
  <div class="app">
    <h1>我的網址收藏</h1>
    <div class="form-card">
      <input
        v-model="url"
        type="url"
        placeholder="貼上網址，按下 Enter 或新增"
        @keyup.enter="addBookmark"
      />
      <button @click="addBookmark">＋ 新增</button>
    </div>

    <div v-if="bookmarks.length" class="list-container">
      <ul>
        <li v-for="(bm, i) in bookmarks" :key="i" class="bookmark-card">
          <a :href="bm.url" target="_blank">{{ bm.url }}</a>
          <button class="delete-btn" @click="deleteBookmark(i)">✕</button>
        </li>
      </ul>
      <button class="clear-btn" @click="clearAll">清空全部</button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue';

const url = ref('');
const bookmarks = ref([]);

onMounted(() => {
  const stored = localStorage.getItem('bookmarks');
  if (stored) bookmarks.value = JSON.parse(stored);
});

watch(
  bookmarks,
  (newVal) => {
    localStorage.setItem('bookmarks', JSON.stringify(newVal));
  },
  { deep: true }
);

const addBookmark = () => {
  const link = url.value.trim();
  if (!link) return;
  try {
    new URL(link);
  } catch {
    return alert('請輸入有效網址');
  }
  bookmarks.value.unshift({ url: link });
  url.value = '';
};

const deleteBookmark = (i) => {
  bookmarks.value.splice(i, 1);
};

const clearAll = () => {
  if (confirm('確定要清空全部嗎？')) bookmarks.value = [];
};
</script>

<style scoped>
.app {
  max-width: 480px;
  margin: 40px auto;
  font-family: 'Segoe UI', sans-serif;
  text-align: center;
}
h1 {
  margin-bottom: 24px;
  color: #333;
}
.form-card {
  display: flex;
  gap: 8px;
  margin-bottom: 24px;
}
input {
  flex: 1;
  padding: 12px;
  font-size: 16px;
  border: 2px solid #ddd;
  border-radius: 6px;
  transition: border-color 0.2s;
}
input:focus {
  outline: none;
  border-color: #007bff;
}
button {
  padding: 0 16px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  cursor: pointer;
}
button:hover {
  opacity: 0.9;
}
.list-container {
  text-align: left;
}
.bookmark-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: white;
  padding: 12px 16px;
  border-radius: 6px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
  margin-bottom: 8px;
}
.bookmark-card a {
  color: #007bff;
  text-decoration: none;
  word-break: break-all;
}
.delete-btn {
  background: #e53e3e;
  padding: 4px 8px;
}
.delete-btn:hover {
  background: #c53030;
}
.clear-btn {
  margin-top: 12px;
  background: #e53e3e;
  width: 100%;
}
.clear-btn:hover {
  background: #c53030;
}
</style>
