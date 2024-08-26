<template>
  <div :class="containerClass">
    <label v-if="label" :class="labelClass">{{ label }}</label>
    <input
      :type="type"
      :class="inputClass"
      :placeholder="type === 'text' ? placeholder : undefined"
      :disabled="disabled"
      :checked="type === 'checkbox' || type === 'radio' ? modelValue === value : undefined"
      :value="type === 'text' ? modelValue : value"
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
    validator: (value: string) => ['text', 'checkbox', 'radio'].includes(value)
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
  },
  value: {
    type: [String, Boolean],
    default: ''
  }
})

const emit = defineEmits(['update:modelValue'])

const containerClass = computed(() => {
  return props.type === 'checkbox' || props.type === 'radio'
    ? 'form-check d-flex align-items-center'
    : 'form-group'
})

const labelClass = computed(() => {
  return props.type === 'checkbox' || props.type === 'radio' ? 'form-check-label' : ''
})

const inputClass = computed(() => {
  return props.type === 'checkbox' || props.type === 'radio' ? 'form-check-input' : 'form-control'
})

const onInput = (event: Event) => {
  if (props.type === 'text') {
    const target = event.target as HTMLInputElement
    emit('update:modelValue', target.value)
  }
}

const onChange = (event: Event) => {
  const target = event.target as HTMLInputElement
  if (props.type === 'checkbox' || props.type === 'radio') {
    emit('update:modelValue', target.checked ? props.value : '')
  }
}
</script>

<style scoped>
/* Estilos adicionais podem ser aplicados aqui, se necessário */
</style>
