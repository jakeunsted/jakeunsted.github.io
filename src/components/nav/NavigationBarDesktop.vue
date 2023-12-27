<template>
  <v-app>
    <v-app-bar app color="primary">
      <v-switch v-model="isDarkMode" class="ml-2 theme-switch" @click="toggleTheme"></v-switch>
      <v-toolbar-title class="text-left">Jake Unsted</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/" text :class="{ 'primary': currentPage === 'Home' }">Home</v-btn>
      <!-- <v-btn to="/projects" text :class="{ 'primary': currentPage === 'Projects' }">Projects</v-btn> -->
      <v-menu class="ml-2">
        <template v-slot:activator="{ props }">
          <v-btn
            :class="{ 'primary': currentPage === 'Projects' }"
            v-bind="props"
          >
            Projects
          </v-btn>
        </template>
        <v-list>
          <v-list-item
            v-for="(item, index) in items"
            :key="index"
            :value="index"
          >
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-btn to="/contact" text :class="{ 'primary': currentPage === 'Contact' }">Contact</v-btn>
    </v-app-bar>

    <router-view></router-view>
  </v-app>
</template>

<script>
import { computed } from 'vue'
import { useTheme } from 'vuetify'

export default {
  name: 'NavigationBarDesktop',
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
  data: () => ({
    items: [
      { title: 'GTM Page Scraper', to: '/projects' },
      { title: 'Parental Control Server', to: '/' },
    ],
  }),
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
