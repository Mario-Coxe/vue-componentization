<!-- src/components/button/Button.vue -->
<template>
  <button :class="['btn', buttonClasses]" :disabled="isDisabled" @click="handleClick">
    <i v-if="icon" :class="iconClass"></i>
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, computed } from 'vue'

const props = defineProps({
  type: {
    type: String,
    default: 'primary'
  },
  size: {
    type: String,
    default: 'md'
  },
  isDisabled: {
    type: Boolean,
    default: false
  },
  icon: {
    type: String,
    default: null
  }
})

const emit = defineEmits(['click'])

const buttonClasses = computed(() => {
  return [`btn-${props.type}`, sizeClass.value, { disabled: props.isDisabled }]
})

const sizeClass = computed(() => {
  return props.size === 'sm' ? 'btn-sm' : props.size === 'lg' ? 'btn-lg' : ''
})

const iconClass = computed(() => {
  return props.icon ? `fa ${props.icon}` : ''
})

const handleClick = (event: Event) => {
  if (!props.isDisabled) {
    emit('click', event)
  }
}
</script>

<style scoped>
button i {
  margin-right: 0.5em;
}
</style>
