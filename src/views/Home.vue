<template>
  <div class="root">
    <Header />
  </div>
</template>

<script>
import Header from '@/includes/Header';

export default {
  name: 'Home',
  components: {
    Header
  }
}
</script>

<style>
  .root {
    background-color: #84C2C0;
  }
</style>