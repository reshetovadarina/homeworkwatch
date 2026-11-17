<script setup>
import { ref, watch } from 'vue'

/*const userName = ref('Дарина')

watch(userName, (newValue, oldValue) => {
  console.log('Нове ім’я:', newValue)
  console.log('Старе ім’я:', oldValue)
}) */


const STORAGE_KEY = 'saved_user_name'

const userName = ref(localStorage.getItem(STORAGE_KEY) || '')

watch(userName, (newValue) => {
  localStorage.setItem(STORAGE_KEY, newValue)
})

const settings = ref({ dark: false })

watch(settings, (val) => {
  console.log('З deep:', val.dark)
}, { deep: true })

</script>

<template>
 <input v-model="userName" placeholder="Введіть ім'я" />
  <input type="checkbox" v-model="settings.dark" />



</template>
