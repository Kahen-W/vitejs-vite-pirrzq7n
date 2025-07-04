# 📌 收藏網址小工具（Vue 3 + Composition API）

這是一個使用 Vue 3 Composition API 製作的收藏網址小工具。你可以快速將常用網址儲存到清單中，支援點擊跳轉、刪除、清空全部，並使用 localStorage 確保資料在重新整理後仍保留。
https://stackblitz.com/edit/vitejs-vite-pirrzq7n?file=src%2FApp.vue


## 🔧 功能介紹

- ✅ 新增收藏：輸入網址後按「新增」或 Enter 鍵即可儲存
- ✅ 顯示清單：以卡片風格展示已收藏的網址
- ✅ 點擊開啟：點網址可直接開啟連結（新分頁）
- ✅ 刪除項目：每筆資料皆可單獨刪除
- ✅ 一鍵清空：支援清空所有收藏（含確認提示）
- ✅ 本地儲存：使用 `localStorage` 保存資料，重整不會消失

## 🎨 設計風格

- 使用現代化卡片風格設計
- 支援漸層按鈕、圓角 UI、hover 效果
- 簡潔介面，操作直覺

## 🗂️ 技術資訊

- 框架：Vue 3 + Composition API
- 工具：Vite（內建於 StackBlitz）
- 儲存：瀏覽器 localStorage
