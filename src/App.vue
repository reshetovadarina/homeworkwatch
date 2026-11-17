<script setup>
import { ref, watch, watchEffect, computed  } from 'vue'

/*const userName = ref('Дарина')
watch(userName, (newValue, oldValue) => {
  console.log('Нове ім’я:', newValue)
  console.log('Старе ім’я:', oldValue)
}) */


/*const STORAGE_KEY = 'saved_user_name'
const userName = ref(localStorage.getItem(STORAGE_KEY) || '')
watch(userName, (newValue) => {
  localStorage.setItem(STORAGE_KEY, newValue)
})*/


/* const settings = ref({ dark: false })
watch(settings, (val) => {
  console.log('З deep:', val.dark)
}, { deep: true }) */


/*const STORAGE_KEY = 'saved_user_name'
const userName = ref(localStorage.getItem(STORAGE_KEY) || '')
watchEffect(() => {
  localStorage.setItem(STORAGE_KEY, userName.value)
})
*/

/*const themeLabel = computed(() => {
  return settings.value.dark ? 'Темна тема' : 'Світла тема'
}) */

</script>

<template>
 <input v-model="userName" placeholder="Введіть ім'я" />
 <input type="checkbox" v-model="settings.dark" />
   <label>
    <input type="checkbox" v-model="settings.dark" />
    Поточний режим: {{ themeLabel }}
  </label>


</template>
