<template>
  <div class="date-filter">
    <input type="date" v-model="startDate" class="form-control" placeholder="Data inicial" />
    <span class="mx-2">até</span>
    <input type="date" v-model="endDate" class="form-control" placeholder="Data final" />
  </div>
</template>

<script setup lang="ts">
import { ref, defineEmits } from 'vue'

const emit = defineEmits(['filter', 'clear'])

const startDate = ref<string | null>(null)
const endDate = ref<string | null>(null)

const applyFilter = () => {
  emit('filter', { startDate: startDate.value, endDate: endDate.value })
}

const clearFilter = () => {
  startDate.value = null
  endDate.value = null
  emit('clear')
}
</script>

<style scoped>
.date-filter {
  display: flex;
  align-items: center;
}

.date-filter input {
  width: 150px;
}

.date-filter button {
  white-space: nowrap;
}
</style>
