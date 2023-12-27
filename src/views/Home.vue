<template>
  <NavigationBarDesktop current-page="Home" />
  <h1>home</h1>
</template>

<script>
  import NavigationBarDesktop from '@/components/nav/NavigationBarDesktop.vue'
  import NavigationBarMobile from '@/components/nav/NavigationBarMobile.vue'
  export default {
  components: {
    NavigationBarDesktop,
    NavigationBarMobile
  },
  data() {
    return {
      darkMode: false, // Initial value for dark mode
    };
  },
  watch: {
    darkMode(newValue) {
      // Update the theme based on the darkMode value
      this.$vuetify.theme.dark = newValue;
    },
  },
};
</script>
