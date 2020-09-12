<template>
  <div class="home">
    <Header />
    <div class="container">
      <Playing v-bind:playing="playing"/>
      <div class="stations-title">
        <div class="title">
          Radio stations
        </div>
        <div class="rectangle"></div>
      </div>
      <Stations v-bind:data="data" v-on:change-radio="changeRadio"/>
    </div>
    <Footer />
  </div>
</template>

<script>
// Dependencies
import axios from 'axios';

// Includes
import Header from '@/includes/Header';
import Footer from '@/includes/Footer';

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
    Stations,
    Footer
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
  
  .container {
    padding-top: 6%;
    min-height: calc(100vh - 82px);
    margin-left: 5%;
  }

  .stations-title {
    margin-left: 5%;
    margin-top: 5%;
  }

  .stations-title .title {
    font-size: 36px; 
    font-family: "Teko", sans-serif;
    color: #fff;
  }

  .stations-title .rectangle {
      width: 240px;
      height: 10px;
      margin-bottom: 20px;
      background-color: #fff;
  }
</style>