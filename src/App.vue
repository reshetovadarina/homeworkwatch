<script setup>
import { ref, watch, watchEffect, computed } from 'vue'

// 1. Ім'я користувача з підтягуванням із localStorage
const STORAGE_KEY = 'saved_user_name'
const userName = ref(localStorage.getItem(STORAGE_KEY) || '')

// 2. Звичайний watch: виводить у консоль старе та нове значення
watch(userName, (newValue, oldValue) => {
  console.log('Ім’я змінилося:', { старе: oldValue, нове: newValue })
})

// 3. watchEffect: автоматично зберігає ім'я в localStorage при кожній зміні
watchEffect(() => {
  localStorage.setItem(STORAGE_KEY, userName.value)
})

// 4. Об'єкт налаштувань
const settings = ref({
  dark: false
})

// 5. Watch із deep: true для відстеження змін усередині об'єкта
watch(
  settings,
  (newSettings) => {
    console.log('Налаштування оновлено (deep):', newSettings)
  },
  { deep: true }
)

// 6. Computed: рахує текст теми на основі налаштувань
const themeLabel = computed(() => {
  return settings.value.dark ? 'Темна тема' : 'Світла тема'
})
</script>

<template>
  <div style="padding: 20px; font-family: sans-serif;">
    <div style="margin-bottom: 20px;">
      <label for="username">Ім'я користувача: </label>
      <input
        id="username"
        v-model="userName"
        type="text"
        placeholder="Введіть ім'я"
      />
    </div>

    <div>
      <label>
        <input type="checkbox" v-model="settings.dark" />
        Увімкнути темну тему
      </label>
      <p>Поточний режим: <strong>{{ themeLabel }}</strong></p>
    </div>
  </div>
</template>
