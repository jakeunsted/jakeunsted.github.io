<template>
  <v-app>
    <div class="nav-bar">
      <NavigationBarMobile v-if="isMobile" current-page="Home" />
      <NavigationBarDesktop v-else current-page="Home" />
    </div>
    
    <WaveBackground class="wave-background"/>
  </v-app>
</template>

<script>
  import { ref, onMounted, onBeforeUnmount } from 'vue'
  import NavigationBarDesktop from '@/components/nav/NavigationBarDesktop.vue'
  import NavigationBarMobile from '@/components/nav/NavigationBarMobile.vue'
  import WaveBackground from '@/components/background/WaveBackground.vue'
  export default {
  components: {
    NavigationBarDesktop,
    NavigationBarMobile,
    WaveBackground
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

<style scoped>
.nav-bar {
  position: relative;
  z-index: 2;
}
</style>