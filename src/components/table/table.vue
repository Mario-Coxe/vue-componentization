<template>
  <div class="container">
    <div class="col-12">
      <div class="card">
        <div class="card-header d-flex justify-content-between align-items-center">
          <h3 class="card-title">{{ title }}</h3>

          <div v-if="search" class="card-tools">
            <div class="input-group input-group-sm btn-sm optionbox">
              <select v-model="selectedColumn" class="form-select form-select-sm me-2">
                <option v-for="column in columns" :key="column.key" :value="column.key">
                  {{ column.label }}
                </option>
              </select>
              <SearchInput placeholder="Pesquisar..." class="form-control" />

              <button class="btn btn-sm btn-primary ms-2">
                <i class="fas fa-search"></i> Filtrar
              </button>
              <button class="btn btn-sm btn btn-outline-danger ms-2">
                <i class="fas fa-eraser"></i> Limpar
              </button>
              <button
                v-if="showRegisterButton"
                class="btn btn-sm btn-outline-dark ms-2"
                :disabled="registerButtonIsDisabled"
              >
                <i class="fas fa-plus"></i> Registrar
              </button>
            </div>
          </div>
        </div>
        <div class="card-body table-responsive p-0">
          <table class="table table-hover text-nowrap">
            <thead>
              <tr class="text-center">
                <th>ID</th>
                <th v-for="column in columns" :key="column.key">{{ column.label }}</th>
                <th v-if="buttonActions">Ações</th>
              </tr>
            </thead>

            <tbody class="text-center">
              <tr v-for="(row, index) in data" :key="index">
                <td>{{ index + 1 }}</td>
                <!-- Exibe o número do registro começando de 1 -->
                <td v-for="column in columns" :key="column.key">{{ row[column.key] }}</td>
                <td v-if="buttonActions" class="d-flex align-items-center">
                  <div class="input-group-append p-1">
                    <Button
                      type="btn-sm btn-primary"
                      size="btn-lg"
                      isDisabled="editIsDisabled"
                      icon="fas fa-edit"
                    >
                      Editar
                    </Button>
                  </div>

                  <Button
                    type="btn-sm btn-danger ms-3"
                    size="btn-lg"
                    isDisabled="deleteIsDisabled"
                    icon="fas fa-trash"
                  >
                    Eliminar
                  </Button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, defineProps } from 'vue'
import SearchInput from '../search-input/search-input.vue'
import Button from '../button/button.vue'
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
  buttonActions: {
    type: Boolean,
    default: false
  },
  editIsDisabled: {
    type: Boolean,
    default: false
  },
  deleteIsDisabled: {
    type: Boolean,
    default: false
  },
  showRegisterButton: {
    type: Boolean,
    default: true
  },
  registerButtonIsDisabled: {
    type: Boolean,
    default: false
  }
})

const selectedColumn = ref(props.columns[0].key)

const editRow = (index: number) => {
  console.log('Editar linha', index)
}

const deleteRow = (index: number) => {
  console.log('Eliminar linha', index)
}
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
