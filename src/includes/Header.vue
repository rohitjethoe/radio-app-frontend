<template>
  <div class="header" v-bind:class="{ opened : navStatus}">
      <div class="nav">
        <div @click="openNavBar()" class="burger-icon">
            <div class="rect rect-1"></div>
            <div class="rect"></div>
            <div class="rect rect-3"></div>
        </div>
      </div>
      <div class="logo">
        Radioworld
      </div>
      <div class="radio">
      </div>
  </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            navStatus: false
        }
    },
    methods: {
        openNavBar() {
            this.navStatus = !this.navStatus;
        }
    }
}
</script>

<style scoped>
    .opened .rect-1 {
        transform: translateY(8px);
    }

    .opened .rect-3 {
        transform: translateY(-8px);
    }

    .burger-icon {
        padding: 14px;
    }

    .burger-icon:hover {
        cursor: pointer;
    }

    .burger-icon .rect {
        width: 30px;
        margin: 4.2px 0px;
        height: 3.5px;
        background-color: #fff;
        transition: 0.2s all;
    }

    .nav {
        float: left;
    }

    .logo {
        text-align: center;
        font-family: 'Teko', sans-serif;
        font-size: 32px;
        text-transform: uppercase;
        padding-top: 5px;
        color: #fff;
    }
    
    .logo::selection {
        background-color: #84C2C0;
    }

    .radio {
        float: right;
        font-size: 24px;
    }

    .header::after {
        clear: both;
        content: "";
        display: table;
    }
</style>