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
        <!-- /.card-header -->
        <div class="card-body table-responsive p-0">
          <table class="table table-hover text-nowrap">
            <thead>
              <tr>
                <th v-for="column in columns" :key="column.key">{{ column.label }}</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(row, index) in filteredData" :key="index">
                <td v-for="column in columns" :key="column.key">{{ row[column.key] }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <!-- /.card-body -->
      </div>
      <!-- /.card -->
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, defineProps } from 'vue'
import SearchInput from '../search-input/search-input.vue'

// Props
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
  },
  searchPlaceholder: {
    type: String,
    default: 'Search...'
  }
})

const selectedColumn = ref(props.columns[0].key)
const searchQuery = ref('')

// Filtered data
const filteredData = computed(() => {
  if (!searchQuery.value) return props.data
  return props.data.filter((row) => {
    return String(row[selectedColumn.value]).toLowerCase().includes(searchQuery.value.toLowerCase())
  })
})

// Methods
const onSearch = () => {
  // Ação de busca se necessário
}
</script>

<style scoped>
.optionbox {
  display: flex;
  align-items: center;
  gap: 0.5rem; /* Espaço entre o select e o campo de pesquisa */
}

.optionbox select {
  background: #ffffff; /* Cor branca para o fundo */
  color: #000000; /* Texto preto para contraste */
  padding: 5px; /* Reduzido o padding */
  width: 150px; /* Largura menor */
  height: 35px; /* Altura menor */
  border: 1px solid #ccc; /* Borda cinza clara */
  font-size: 14px; /* Tamanho da fonte reduzido */
  box-shadow: none; /* Removido o box-shadow */
  outline: none;
}

.optionbox select:focus {
  border-color: #007bff; /* Cor de foco padrão do Bootstrap */
  box-shadow: 0 0 0 0.2rem rgba(38, 143, 255, 0.25); /* Sombra leve de foco */
}
</style>
