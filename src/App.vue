<script setup lang="ts">
import MyButton from '@/components/button/Button.vue'

const handleButtonClick = () => {
  console.log('Botão foi clicado!')
}
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col-md">
        <div class="card">
          <div class="card-header">
            <h5 class="card-title">Usando Button</h5>
          </div>
          <div class="card-body text-center">
            <MyButton
              type="success"
              size="btn-lg"
              :isDisabled="false"
              icon="fas fa-edit"
              @click="handleButtonClick"
            >
              Editar
            </MyButton>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
