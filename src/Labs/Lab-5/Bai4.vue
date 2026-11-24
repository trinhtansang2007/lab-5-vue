<template>
  <div :class="['theme-shell', theme]">
    <div class="d-flex flex-wrap justify-content-between align-items-center gap-2 mb-3">
      <p class="mb-0">ThemeProvider đang cung cấp chủ đề cho component con.</p>
      <button type="button" class="btn btn-sm btn-outline-light theme-toggle" @click="toggleTheme">
        Đổi chủ đề
      </button>
    </div>
    <slot :theme="theme"></slot>
  </div>
</template>

<script setup>
import { provide, ref } from 'vue'

const theme = ref('dark-theme')

provide('theme', theme)

const toggleTheme = () => {
  theme.value = theme.value === 'dark-theme' ? 'light-theme' : 'dark-theme'
}
</script>
