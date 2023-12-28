<template>
  <section class="curve">
    <slot></slot>
  </section>
</template>

<script>
export default {
  name: 'WaveBackground',
  props: {
    color: {
      type: String,
      default: '#1c1c1c'
    }
  },
}
</script>

<style>
.curve {
  background-image: url('../../assets/waves/wave-haikei.svg');
  /* background-position: center; */
  background-size: contain;
  height: 100%;
  /* margin-top: -200px */
}
</style>