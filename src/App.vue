<script setup lang="ts">
import Button from '@/components/button/Button.vue'
import Widget from './components/box/Box.vue'

// Função para manipular o clique do botão
const handleButtonClick = () => {
  console.log('Botão foi clicado!')
}
</script>

<template>
  <div class="container mt-4">
    <div class="row justify-content-center">
      <!-- Card para o componente Button -->
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
    </div>
  </div>
</template>

<style scoped>
/* Adicione estilos personalizados aqui, se necessário */
</style>
