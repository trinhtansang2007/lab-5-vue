<script setup>
import { ref } from 'vue'
import Bai1 from './Labs/Lab-5/Bai1.vue'
import Bai2 from './Labs/Lab-5/Bai2.vue'
import Bai3 from './Labs/Lab-5/Bai3.vue'
import Bai4 from './Labs/Lab-5/Bai4.vue'

const currentBai = ref(1)
const baiList = [
  { id: 1, label: 'Bài 1 - Props' },
  { id: 2, label: 'Bài 2 - Emit' },
  { id: 3, label: 'Bài 3 - Slot' },
  { id: 4, label: 'Bài 4 - Provide / Inject' },
]

const sampleBooks = [
  {
    id: '1',
    title: 'Cuốn sách 1',
    author: 'Tác giả A',
    price: 150000,
    category: 'Fiction',
  },
  {
    id: '2',
    title: 'Lập trình Vue 3',
    author: 'Nguyễn Văn B',
    price: 220000,
    category: 'Công nghệ',
  },
]

const books = ref([])

const addBook = (book) => {
  books.value.push(book)
}
</script>

<template>
  <main class="page">
    <header class="page-header">
      <p class="eyebrow">FRONT END FRAMEWORK · VUE 3</p>
      <h1>LAB 5 – COMPONENT</h1>
      <p class="subtitle">Props, Emit, Slots và Provide / Inject</p>
    </header>

    <nav class="tabs" aria-label="Chọn bài thực hành">
      <button
        v-for="bai in baiList"
        :key="bai.id"
        type="button"
        :class="['tab-button', { active: currentBai === bai.id }]"
        @click="currentBai = bai.id"
      >
        {{ bai.label }}
      </button>
    </nav>

    <section class="content-panel">
      <div v-if="currentBai === 1">
        <h2>BookCard nhận props</h2>
        <p class="lead-note">
          Component <code>Bai1.vue</code> nhận <code>id</code>, <code>title</code>,
          <code>author</code>, <code>price</code> và <code>category</code>.
        </p>
        <Bai1
          v-for="book in sampleBooks"
          :key="book.id"
          :id="book.id"
          :title="book.title"
          :author="book.author"
          :price="book.price"
          :category="book.category"
        />
      </div>

      <div v-else-if="currentBai === 2">
        <h2>Form thêm sách bằng emit</h2>
        <p class="lead-note">
          <code>Bai2.vue</code> emit sự kiện <code>add-book</code>.
          <code>App.vue</code> lắng nghe và hiển thị danh sách bằng <code>Bai1.vue</code>.
        </p>
        <Bai2 @add-book="addBook" />
        <Bai1
          v-for="(book, index) in books"
          :key="book.id || index"
          :id="book.id || String(index + 1)"
          :title="book.title"
          :author="book.author"
          :price="book.price"
          :category="book.category"
        />
        <p v-if="!books.length" class="empty-state">Chưa có sách. Hãy thêm sách mới.</p>
      </div>

      <div v-else-if="currentBai === 3">
        <h2>Card dùng slot</h2>
        <p class="lead-note">
          <code>Bai3.vue</code> để chỗ trống <code>&lt;slot&gt;</code> cho nội dung tùy chỉnh.
        </p>
        <Bai3>
          <h5 class="card-title">Tiêu đề sách</h5>
          <h6 class="card-subtitle mb-2 text-muted">Tác giả: Tác giả A</h6>
          <p class="card-text">Giá: 150000 VND</p>
          <p class="card-text mb-0">Thể loại: Fiction</p>
        </Bai3>
        <Bai3>
          <h5 class="card-title">Nội dung slot khác</h5>
          <p class="card-text mb-0">
            Cùng một component card, nội dung bên trong được truyền từ component cha.
          </p>
        </Bai3>
      </div>

      <div v-else>
        <h2>Scoped slot và provide / inject</h2>
        <p class="lead-note">
          <code>Bai4.vue</code> provide chủ đề và đưa <code>theme</code> ra scoped slot.
          <code>Bai3.vue</code> inject chủ đề đó khi nằm bên trong.
        </p>
        <Bai4>
          <template #default="{ theme }">
            <h3 :class="theme" class="theme-heading">Chủ đề hiện tại: {{ theme }}</h3>
            <Bai3>
              <h5 class="card-title">Tiêu đề sách</h5>
              <h6 class="card-subtitle mb-2 text-muted">Tác giả: Tác giả A</h6>
              <p class="card-text">Giá: 150000 VND</p>
              <p class="card-text mb-0">Thể loại: Fiction</p>
            </Bai3>
          </template>
        </Bai4>
      </div>
    </section>

    <p class="footer-note">Dữ liệu bài 2 được lưu trong bộ nhớ khi ứng dụng đang chạy.</p>
  </main>
</template>
