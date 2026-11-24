<template>
  <form class="mb-4 book-form" @submit.prevent="submitForm">
    <div class="mb-3">
      <input v-model="title" type="text" class="form-control" placeholder="Tiêu đề" required />
    </div>
    <div class="mb-3">
      <input v-model="author" type="text" class="form-control" placeholder="Tác giả" required />
    </div>
    <div class="mb-3">
      <input
        v-model.number="price"
        type="number"
        min="0"
        class="form-control"
        placeholder="Giá"
        required
      />
    </div>
    <div class="mb-3">
      <input v-model="category" type="text" class="form-control" placeholder="Thể loại" required />
    </div>
    <button type="submit" class="btn btn-primary">Thêm sách</button>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add-book'])

const title = ref('')
const author = ref('')
const price = ref(0)
const category = ref('')

const submitForm = () => {
  if (!title.value.trim() || !author.value.trim() || !category.value.trim()) {
    return
  }

  emit('add-book', {
    id: String(Date.now()),
    title: title.value.trim(),
    author: author.value.trim(),
    price: Number(price.value) || 0,
    category: category.value.trim(),
  })

  title.value = ''
  author.value = ''
  price.value = 0
  category.value = ''
}
</script>
