<script setup lang="ts">
import { toast, type ToastOptions } from 'vue3-toastify'
import { defineProps, defineEmits, watch } from 'vue'

const props = defineProps({
  message: {
    type: String,
    default: 'message'
  },
  type: {
    type: String,
    default: 'success',
    validator: (value: string) => ['success', 'error', 'warning', 'info'].includes(value)
  },
  trigger: {
    type: Boolean,
    default: false
  }
})

const emit = defineEmits(['notificationSent'])

const showToast = () => {
  if (props.type === 'success') {
    toast.success(props.message)
  } else if (props.type === 'error') {
    toast.error(props.message)
  } else if (props.type === 'warning') {
    toast.warning(props.message)
  } else {
    toast.info(props.message)
  }
  emit('notificationSent')
}

watch(
  () => props.trigger,
  (newVal) => {
    if (newVal) {
      showToast()
    }
  }
)
</script>

<template></template>

<style scoped></style>
