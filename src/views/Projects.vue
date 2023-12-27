<template>
  <NavigationBarMobile v-if="isMobile" current-page="Projects" />
  <NavigationBarDesktop v-else current-page="Projects" />
</template>

<script>
  import { ref, onMounted, onBeforeUnmount } from 'vue'
  import NavigationBarDesktop from '@/components/nav/NavigationBarDesktop.vue'
  import NavigationBarMobile from '@/components/nav/NavigationBarMobile.vue'
  export default {
  components: {
    NavigationBarDesktop,
    NavigationBarMobile
  },
  setup() {
    const isMobile = ref(window.innerWidth <= 600);

    const handleResize = () => {
      isMobile.value = window.innerWidth <= 600;
    };

    onMounted(() => {
      window.addEventListener('resize', handleResize);
    });

    onBeforeUnmount(() => {
      window.removeEventListener('resize', handleResize);
    });

    return {
      isMobile,
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
