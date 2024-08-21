<!-- src/components/button/Button.vue -->
<template>
  <button
    :class="['btn', buttonTypeClass, sizeClass, { disabled: isDisabled }]"
    :disabled="isDisabled"
    @click="handleClick"
  >
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

const buttonTypeClass = computed(() => {
  return `btn-${props.type}`
})

const sizeClass = computed(() => {
  switch (props.size) {
    case 'sm':
      return 'btn-sm'
    case 'lg':
      return 'btn-lg'
    default:
      return ''
  }
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
