<template>
  <input
    class="form-control float-right"
    type="text"
    name="table_search"
    :placeholder="placeholder"
    v-model="searchQuery"
  />

  <div class="input-group-append">
    <button type="submit" class="btn btn-default" @click="onSearch">
      <i class="fas fa-search"></i>
    </button>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, ref } from 'vue'

const props = defineProps({
  placeholder: {
    type: String,
    default: 'Digite algo...'
  }
})

const emit = defineEmits(['search'])

const searchQuery = ref('')

const onSearch = () => {
  emit('search', searchQuery.value)
}
</script>

<style scoped></style>
