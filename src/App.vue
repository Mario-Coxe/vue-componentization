<script setup lang="ts">
import Button from '@/components/button/Button.vue'
import Box from './components/box/Box.vue'

// Função de exemplo para lidar com o clique do botão
const handleButtonClick = () => {
  console.log('Botão foi clicado!')
}
</script>

<template>
  <div class="container">
    <!-- Card para o componente Button -->
    <div class="col-md">
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

    <!-- Card para o componente Box -->
    <div class="small-box bg-success">
      <Box
        title="53"
        subtitle="%"
        description="Bounce Rate"
        icon="ion ion-stats-bars"
        boxType="small-box bg-info"
      />
    </div>
  </div>
</template>

<style scoped></style>
