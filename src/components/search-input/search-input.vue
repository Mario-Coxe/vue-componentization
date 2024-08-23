<template>
  <div class="search-input">
    <input type="text" class="form-control" :placeholder="placeholder" v-model="searchQuery" />
    <Button type="primary" size="btn-sm" :isDisabled="false" icon="fa fa-search" @click="onSearch">
    </Button>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, ref } from 'vue'
import Button from '../button/button.vue'

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

<style scoped>
.search-input {
  display: flex;
  align-items: center;
}

.search-input input {
  flex-grow: 1;
  margin-right: 10px;
}

.search-input button {
  padding: 6px 12px;
}
</style>
