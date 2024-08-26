<script setup lang="ts">
import { ref } from 'vue'
import Button from '@/components/button/button.vue'
import Widget from '@/components/box/box.vue'
import SearchInput from '@/components/search-input/search-input.vue'
import Checkbox from '@/components/checkbox/checkbox.vue'

const handleButtonClick = () => {
  console.log('Botão foi clicado!')
}

const searchResult = ref('')
const isChecked = ref(false)

const handleSearch = (query: string) => {
  searchResult.value = query
  console.log('Valor digitado:', query)
  console.log(isChecked.value)
}
</script>

<template>
  <div class="container mt-4">
    <div class="row justify-content-center">
      <div class="col-md-6 mb-4">
        <div class="card">
          <div class="card-header">
            <h5 class="card-title">Usando Button</h5>
          </div>
          <div class="card-body text-center">
            <Button
              type="warning"
              size="btn-lg"
              :isDisabled="false"
              icon="fas fa-edit"
              @click="handleButtonClick"
            >
              Editar
            </Button>
          </div>
        </div>
      </div>

      <!-- Componente SearchInput -->
      <div class="col-md-6 mb-4">
        <SearchInput placeholder="User name..." @search="handleSearch" />
      </div>

      <!-- Linhas e colunas para os boxes -->
      <div class="row">
        <!-- Box 1 -->
        <div class="col-md-6">
          <Widget
            title="150"
            description="New Orders"
            icon="fas fa-shopping-cart"
            boxType="bg-info"
          />
        </div>

        <!-- Box 2 -->
        <div class="col-md-6">
          <Widget
            title="53"
            subtitle="%"
            description="Bounce Rate"
            icon="ion ion-stats-bars"
            boxType="bg-success"
          />
        </div>

        <!-- Box 3 -->
        <div class="col-md-6">
          <Widget
            title="44"
            description="User Registrations"
            icon="fas fa-user-plus"
            boxType="bg-warning"
          />
        </div>

        <!-- Box 4 -->
        <div class="col-md-6">
          <Widget
            title="65"
            description="Unique Visitors"
            icon="fas fa-chart-pie"
            boxType="bg-danger"
          />
        </div>
      </div>

      <div class="row">
        <div class="container mt-4">
          <Checkbox id="checkbox1" label="Aceito os termos e condições" v-model="isChecked" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
