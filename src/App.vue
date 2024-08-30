<script setup lang="ts">
import { ref } from 'vue'
import { toast, type ToastOptions } from 'vue3-toastify'
import app_button from './components/app_button/app_button.vue'
import app_widget from './components/app_widget/app_widget.vue'
import app_searchInput from './components/app_search-input/app_search-input.vue'
import app_checkbox from './components/app_checkbox/app_checkbox.vue'
import app_select from './components/app_select/app_select.vue'
import app_input from './components/app_input/app_input.vue'
import app_genericInput from './components/app_generic-input/app_generic-input.vue'
import app_table from './components/app_table/app_table.vue'
import app_toast_alert from './components/app_toast_alert/app_toast_alert.vue'

const handleButtonClick = () => {
  console.log('selects >', selectedValue.value)
}

const searchResult = ref('')
const isChecked = ref(false)
const textValue = ref('')
const inputGeneric = ref()

const handleSearch = (query: string) => {
  searchResult.value = query
  console.log('Valor digitado:', query)
  console.log(isChecked.value)
  console.log(selectedValue.value)
  console.log(textValue.value)
}

const dropdownOptions = ref([
  { label: 'Opção 1', value: '1' },
  { label: 'Opção 2', value: 2 },
  { label: 'Opção 3', value: 3 }
])

const selectedValue = ref<string | number>()

const tableColumns = [
  { key: 'user', label: 'User' },
  { key: 'date', label: 'Date' },
  { key: 'status', label: 'Status' },
  { key: 'reason', label: 'Reason' }
]

const tableData = [
  {
    id: 183,
    user: 'John Doe',
    date: '11-7-2014',
    status: 'Approved',
    reason: 'Bacon ipsum dolor sit amet.'
  },
  {
    id: 219,
    user: 'Alexander Pierce',
    date: '11-7-2014',
    status: 'Pending',
    reason: 'Bacon ipsum dolor sit amet.'
  },
  {
    id: 657,
    user: 'Bob Doe',
    date: '11-7-2014',
    status: 'Approved',
    reason: 'Bacon ipsum dolor sit amet.'
  },
  {
    id: 175,
    user: 'Mike Doe',
    date: '11-7-2014',
    status: 'Denied',
    reason: 'Bacon ipsum dolor sit amet.'
  }
]

const notificationMessage = ref('Operação realizada com sucesso!')
const notificationType = ref('warning')
const notificationTrigger = ref(false)

const notifyUser = () => {
  notificationTrigger.value = true
}

const handleNotificationSent = () => {
  console.log('Notificação foi enviada!')
  notificationTrigger.value = false
}
</script>

<template>
  <button @click="notifyUser">Enviar Notificação</button>
  <app_toast_alert
    :message="notificationMessage"
    :type="notificationType"
    :trigger="notificationTrigger"
    @notificationSent="handleNotificationSent"
  />

  <!--
    <app_table
    :title="'Users'"
    :columns="tableColumns"
    :data="tableData"
    :search="true"
    :buttonActions="true"
    :editIsDisabled="true"
    :registerButtonIsDisabled="true"
    :showRegisterButton="true"
    :isRangeByDateFilter="false"
  />
  
  <div class="card-body text-center">
    <app_button
      type="warning"
      size="btn-lg"
      :isDisabled="false"
      icon="fas fa-edit"
      @click="handleButtonClick"
    >
      Editar
    </app_button>
  </div>

  <app_select
    :options="dropdownOptions"
    :placeholder="'Selecione a opção'"
    v-model="selectedValue"
  />

  <div>
    <app_widget
      title="53"
      subtitle="%"
      description="Bounce Rate"
      icon="ion ion-stats-bars"
      boxType="bg-success"
    />
  </div>


  <app_table
    :title="'Users'"
    :columns="tableColumns"
    :data="tableData"
    :search="true"
    :buttonActions="true"
    :editIsDisabled="true"
    :registerButtonIsDisabled="true"
    :showRegisterButton="true"
    searchPlaceholder="Search items..."
  />


  <div class="container mt-4">
    <div class="row justify-content-center">
      <div class="col-md-6 mb-4">
        <div class="card">
          <div class="card-header">
            <h5 class="card-title">Usando Button</h5>
          </div>
          <div class="card-body text-center">
            <app_button
              type="warning"
              size="btn-lg"
              :isDisabled="false"
              icon="fas fa-edit"
              @click="handleButtonClick"
            >
              Editar
            </app_button>
          </div>
        </div>
      </div>

      <div class="col-md-6 mb-4">
        <SearchInput placeholder="User name..." @search="handleSearch" />
      </div>

      <div class="row">
        <div class="col-md-6">
          <app_widget
            title="150"
            description="New Orders"
            icon="fas fa-shopping-cart"
            boxType="bg-info"
          />
        </div>

        <div class="col-md-6">
          <app_widget
            title="53"
            subtitle="%"
            description="Bounce Rate"
            icon="ion ion-stats-bars"
            boxType="bg-success"
          />
        </div>

        <div class="col-md-6">
          <app_widget
            title="44"
            description="User Registrations"
            icon="fas fa-user-plus"
            boxType="bg-warning"
          />
        </div>

        <div class="col-md-6">
          <app_widget
            title="65"
            description="Unique Visitors"
            icon="fas fa-chart-pie"
            boxType="bg-danger"
          />
        </div>
      </div>

      <div class="row">
        <div class="container mt-4">
          <app_checkbox id="checkbox1" label="Aceito os termos e condições" v-model="isChecked" />
        </div>

 
        <app_input
          label="Text Disabled"
          placeholder="Enter ..."
          :disabled="false"
          v-model="textValue"
        />

        <app_genericInput type="text" label="Text Input" v-model="textValue" placeholder="Enter text" />
        <app_genericInput
          type="checkbox"
          label="Text Input"
          v-model="inputGeneric"
          placeholder="digite"
        />
        <app_genericInput
          type="radio"
          label="Text Input"
          v-model="inputGeneric"
          placeholder="digite"
        />
      </div>
    </div>
  </div>
  !-->
</template>

<style scoped></style>
