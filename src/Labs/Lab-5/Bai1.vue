<template>
  <div class="card mb-3 book-card">
    <div class="card-body">
      <p class="card-text text-muted mb-1">Mã sách: {{ id }}</p>
      <h5 class="card-title">{{ title }}</h5>
      <h6 class="card-subtitle mb-2 text-muted">Tác giả: {{ author }}</h6>
      <p class="card-text">Giá: {{ price }} VND</p>
      <p class="card-text mb-0">Thể loại: {{ category }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  id: {
    type: [String, Number],
    default: '',
  },
  title: String,
  author: String,
  price: Number,
  category: String,
})
</script>
