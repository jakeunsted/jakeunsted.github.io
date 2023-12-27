<template>
  <NavigationBar current-page="Home" />
  <h1>home</h1>
</template>

<script>
  import NavigationBar from '@/components/NavigationBar.vue'
  export default {
  components: {
    NavigationBar
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
