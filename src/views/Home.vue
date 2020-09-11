<template>
  <div class="home">
    <Header />
    <div class="container">
      <Playing v-bind:playing="playing"/>
      <Stations v-bind:data="data" v-on:change-radio="changeRadio"/>
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
      playing: {
        id: 0,
        name: "Radio Mix Bhakti",
        url: "http://91.121.222.81:8342/stream?type=http&nocache=1266"
      },
    }
  },
  components: {
    Header,
    Playing,
    Stations
  },
  methods: {
    changeRadio(radio) {
      this.playing = radio;
    }
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

  .home {
    background-color: #84C2C0;
  }
  
</style>