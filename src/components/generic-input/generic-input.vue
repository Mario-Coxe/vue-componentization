<template>
  <div :class="containerClass">
    <label v-if="label" :class="labelClass">{{ label }}</label>
    <input
      :type="type"
      :class="inputClass"
      :placeholder="type !== 'checkbox' ? placeholder : undefined"
      :disabled="disabled"
      :checked="type === 'checkbox' ? (modelValue as boolean) : undefined"
      :value="type !== 'checkbox' ? (modelValue as string) : undefined"
      @input="onInput"
      @change="onChange"
    />
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, computed } from 'vue'

const props = defineProps({
  type: {
    type: String,
    default: 'text',
    validator: (value: string) => ['text', 'checkbox'].includes(value)
  },
  label: {
    type: String,
    default: ''
  },
  placeholder: {
    type: String,
    default: 'Enter ...'
  },
  disabled: {
    type: Boolean,
    default: false
  },
  modelValue: {
    type: [String, Boolean],
    default: ''
  }
})

const emit = defineEmits(['update:modelValue'])

const containerClass = computed(() => {
  return props.type === 'checkbox' ? 'form-check d-flex align-items-center' : 'form-group'
})

const labelClass = computed(() => {
  return props.type === 'checkbox' ? 'form-check-label' : ''
})

const inputClass = computed(() => {
  return props.type === 'checkbox' ? 'form-check-input' : 'form-control'
})

const onInput = (event: Event) => {
  if (props.type !== 'checkbox') {
    const target = event.target as HTMLInputElement
    emit('update:modelValue', target.value)
  }
}

const onChange = (event: Event) => {
  if (props.type === 'checkbox') {
    const target = event.target as HTMLInputElement
    emit('update:modelValue', target.checked)
  }
}
</script>

<style scoped></style>
