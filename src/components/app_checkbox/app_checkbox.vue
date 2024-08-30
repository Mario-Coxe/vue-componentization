<template>
  <div class="form-check d-flex align-items-center">
    <input
      class="form-check-input me-2"
      :type="'checkbox'"
      :id="id"
      :checked="modelValue"
      @change="onChange"
    />
    <label class="form-check-label" :for="id">{{ label }}</label>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  id: {
    type: String,
    required: true
  },
  label: {
    type: String,
    required: true
  },
  modelValue: {
    type: Boolean,
    default: false
  }
})

const emit = defineEmits(['update:modelValue'])

const onChange = (event: Event) => {
  const target = event.target as HTMLInputElement
  emit('update:modelValue', target.checked)
}
</script>

<style scoped>
.form-check-label {
  cursor: pointer;
}
</style>
