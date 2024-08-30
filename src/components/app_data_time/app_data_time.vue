<template>
  <div class="date-filter" v-if="isRangeByDate">
    <input
      type="date"
      v-model="startDate"
      @change="emitDates"
      class="form-control"
      placeholder="Data inicial"
    />
    <span class="mx-2">até</span>
    <input
      type="date"
      v-model="endDate"
      @change="emitDates"
      class="form-control"
      placeholder="Data final"
    />
  </div>

  <div class="date-filter" v-if="!isRangeByDate">
    <input
      type="date"
      v-model="createdAt"
      @change="emitDates"
      class="form-control"
      placeholder="Data inicial"
    />
  </div>
</template>

<script setup lang="ts">
import { ref, defineEmits, defineProps } from 'vue'

const emit = defineEmits(['getDataTime'])

const props = defineProps({
  isRangeByDate: {
    type: Boolean,
    default: false
  }
})

const startDate = ref<string | null>(null)
const endDate = ref<string | null>(null)
const createdAt = ref<string | null>(null)

const emitDates = () => {
  emit('getDataTime', {
    startDate: startDate.value,
    endDate: endDate.value,
    createdAt: createdAt.value
  })
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
</style>
