<template>
  <v-app>
    <v-app-bar app color="primary">
      <v-switch v-model="isDarkMode" class="ml-2 theme-switch" @click="toggleTheme"></v-switch>
      <v-toolbar-title class="text-left">Jake Unsted</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/" text :class="{ 'primary': currentPage === 'Home' }">Home</v-btn>
      <v-btn to="/projects" text :class="{ 'primary': currentPage === 'Projects' }">Projects</v-btn>
      <v-btn to="/contact" text :class="{ 'primary': currentPage === 'Contact' }">Contact</v-btn>
    </v-app-bar>

    <router-view></router-view>
  </v-app>
</template>

<script>
import { computed } from 'vue'
import { useTheme } from 'vuetify'

export default {
  name: 'AppNavbar',
  props: {
    currentPage: {
      type: String,
      required: true,
    },
  },
  setup() {
    const theme = useTheme()

    function toggleTheme () {
      theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark'
    }

    const isDarkMode = computed(() => theme.global.current.value.dark);

    return {
      toggleTheme,
      isDarkMode
    }
  },
  data() {
    return {
      darkMode: false, // Initial value for dark mode
    };
  },

};
</script>

<style scoped>
.primary {
  color: white;
}
.theme-switch {
  display: flex;
  max-width: 50px;
}
</style>
