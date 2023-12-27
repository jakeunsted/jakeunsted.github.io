<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app color="primary">
      <v-list>
        <v-list-item to="/" :class="{ 'primary': currentPage === 'Home' }">
          <v-list-item-title>Home</v-list-item-title>
        </v-list-item>
        <v-list-item to="/contact" :class="{ 'primary': currentPage === 'Contact' }">
          <v-list-item-title>Contact</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item to="/projects" :class="{ 'primary': currentPage === 'Projects' }">
          <v-list-item-title>Projects</v-list-item-title>
        </v-list-item>
        <v-list-item-group>
          <v-list-item
            v-for="(item, index) in items"
            :key="index"
            :value="index"
          >
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="primary">
      <v-switch v-model="isDarkMode" class="ml-2 theme-switch" @click="toggleTheme"></v-switch>
      <v-toolbar-title class="text-left">Jake Unsted</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon @click.stop="drawer = !drawer">
        <v-icon>mdi-menu</v-icon>
      </v-btn>
    </v-app-bar>

    <router-view></router-view>
  </v-app>
</template>

<script>
import { computed } from 'vue'
import { useTheme } from 'vuetify'

export default {
  name: 'NavigationBarMobile',
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
    drawer: false,
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
