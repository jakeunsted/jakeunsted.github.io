<template>
  <router-view />
</template>

<script setup>
  import { useTheme } from 'vuetify'
  const theme = useTheme()
  // set theme to dark
  // theme.global.name.value = 'dark'
</script>
