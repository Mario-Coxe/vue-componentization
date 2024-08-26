<template>
  <div class="container">
    <div class="col-12">
      <div class="card">
        <div class="card-header d-flex justify-content-between align-items-center">
          <h3 class="card-title">{{ title }}</h3>

          <div v-if="search" class="card-tools">
            <div class="input-group input-group-sm optionbox">
              <select v-model="selectedColumn" class="form-select form-select-sm me-2">
                <option v-for="column in columns" :key="column.key" :value="column.key">
                  {{ column.label }}
                </option>
              </select>
              <SearchInput placeholder="Pesquisar..." class="form-control" />
            </div>
          </div>
        </div>
        <div class="card-body table-responsive p-0">
          <table class="table table-hover text-nowrap">
            <thead>
              <tr>
                <th v-for="column in columns" :key="column.key">{{ column.label }}</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(row, index) in data" :key="index">
                <td v-for="column in columns" :key="column.key">{{ row[column.key] }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, defineProps } from 'vue'
import SearchInput from '../search-input/search-input.vue'

const props = defineProps({
  title: {
    type: String,
    default: 'Responsive Hover Table'
  },
  columns: {
    type: Array as () => Array<{ key: string; label: string }>,
    required: true
  },
  data: {
    type: Array as () => Array<Record<string, any>>,
    required: true
  },
  search: {
    type: Boolean,
    default: true
  }
})

const selectedColumn = ref(props.columns[0].key)
</script>

<style scoped>
.optionbox {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.optionbox select {
  background: #ffffff;
  color: #000000;
  padding: 5px;
  width: 150px;
  height: 35px;
  border: 1px solid #ccc;
  font-size: 14px;
  box-shadow: none;
  outline: none;
}

.optionbox select:focus {
  border-color: #007bff;
  box-shadow: 0 0 0 0.2rem rgba(38, 143, 255, 0.25);
}
</style>
