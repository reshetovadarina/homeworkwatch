<script setup>
import { ref, watch } from 'vue'

const userName = ref('Дарина')

watch(userName, (newValue, oldValue) => {
  console.log('Нове ім’я:', newValue)
  console.log('Старе ім’я:', oldValue)
})
</script>

<template>
  <input v-model="userName" placeholder="Введіть ім'я" />
</template>
