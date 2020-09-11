<template>
  <div class="root">
    <Header />
    <div class="container">
      <Playing />
      <Stations v-bind:data="data"/>
    </div>
  </div>
</template>

<script>
// Dependencies
import axios from 'axios';

// Includes
import Header from '@/includes/Header';

// Components
import Playing from '@/components/Playing';
import Stations from '@/components/Stations';

export default {
  name: 'Home',
  data() {
    return {
      data: null,
      playing: null,
    }
  },
  components: {
    Header,
    Playing,
    Stations
  },
  mounted() {
    axios.get("https://radiostations-app.herokuapp.com/api/radios")
    .then((res) => {
      this.data = res.data;
    })
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
  }

  .root {
    background-color: #84C2C0;
  }
  
</style>