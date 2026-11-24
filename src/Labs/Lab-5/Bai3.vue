<template>
  <div class="card mb-3 slot-card">
    <div class="card-body">
      <span v-if="theme" class="badge text-bg-secondary mb-3">
        Inject: {{ theme }}
      </span>
      <slot></slot>
    </div>
  </div>
</template>

<script setup>
import { inject } from 'vue'

const theme = inject('theme', null)
</script>
