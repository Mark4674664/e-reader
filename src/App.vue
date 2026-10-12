<script setup>
import { ref, computed } from 'vue'

const books = ref([
  { id: 1, title: '深入理解计算机系统', author: 'Randal E. Bryant', progress: 0.35, cover: '#4F6BED' },
  { id: 2, title: '算法导论', author: 'Thomas H. Cormen', progress: 0.12, cover: '#E8A33D' },
  { id: 3, title: 'Vue.js 设计与实现', author: '霍春阳', progress: 0.78, cover: '#42B883' },
  { id: 4, title: '人类简史', author: '尤瓦尔·赫拉利', progress: 0.55, cover: '#D96D6D' }
])

const currentBook = ref(null)
const keyword = ref('')

const filteredBooks = computed(() => {
  const kw = keyword.value.trim().toLowerCase()
  if (!kw) return books.value
  return books.value.filter(b =>
    b.title.toLowerCase().includes(kw) || b.author.toLowerCase().includes(kw)
  )
})

function openBook(book) {
  currentBook.value = book
}

function closeBook() {
  currentBook.value = null
}
</script>

<template>
  <div class="app">
    <header class="header">
      <h1>📖 电子阅读器</h1>
      <input
        v-model="keyword"
        class="search"
        placeholder="搜索书名或作者..."
      />
    </header>

    <main v-if="!currentBook" class="library">
      <div
        v-for="book in filteredBooks"
        :key="book.id"
        class="book-card"
        @click="openBook(book)"
      >
        <div class="cover" :style="{ background: book.cover }">
          <span class="cover-title">{{ book.title }}</span>
        </div>
        <div class="meta">
          <div class="title">{{ book.title }}</div>
          <div class="author">{{ book.author }}</div>
          <div class="progress-bar">
            <div class="progress" :style="{ width: (book.progress * 100) + '%' }"></div>
          </div>
          <div class="progress-text">{{ Math.round(book.progress * 100) }}%</div>
        </div>
      </div>

      <div v-if="filteredBooks.length === 0" class="empty">
        没有找到匹配的书籍
      </div>
    </main>

    <main v-else class="reader">
      <button class="back-btn" @click="closeBook">← 返回书架</button>
      <h2>{{ currentBook.title }}</h2>
      <div class="author-line">{{ currentBook.author }}</div>
      <div class="content">
        <p>这是 {{ currentBook.title }} 的阅读页面。</p>
        <p>当前进度：{{ Math.round(currentBook.progress * 100) }}%</p>
        <p class="hint">点击左上角"返回书架"回到主页。</p>
      </div>
    </main>

    <footer class="footer">
      共 {{ books.length }} 本书 · Vue 3 构建
    </footer>
  </div>
</template>