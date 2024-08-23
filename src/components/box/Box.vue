<template>
  <div :class="['small-box', boxType]">
    <div class="inner">
      <h3>
        {{ title }}<sup v-if="subtitle" style="font-size: 20px">{{ subtitle }}</sup>
      </h3>
      <p>{{ description }}</p>
    </div>
    <div class="icon">
      <i :class="icon"></i>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'

const props = defineProps({
  title: {
    type: String,
    default: 'Title'
  },
  subtitle: {
    type: String,
    default: ''
  },
  description: {
    type: String,
    default: 'Description'
  },
  icon: {
    type: String,
    default: 'ion ion-stats-bars'
  },
  boxType: {
    type: String,
    default: 'bg-success'
  }
})
</script>

<style scoped></style>
