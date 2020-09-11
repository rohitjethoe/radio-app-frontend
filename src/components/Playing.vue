<template>
  <div class="playing">
      <div class="title">
        📻 {{ playing.name }}
      </div>
      <div class="radio">
        <a target="_blank" rel="noopener" noreferrer :href="playing.url" class="radio-url">
            Link to radio station source <i class="fas fa-external-link-alt"></i>
        </a> <br>
        <audio controls>
            <source v-bind:src="playing.url">
        </audio>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Playing',
    props: ['playing']
}
</script>

<style>
    .playing {
        margin-left: 5%;
        margin-top: 5%;
        background-color: #fff;
        width: 80%;
        padding: 15px 10px;
        border-radius: 4px;
        box-shadow: 0px 1.5px 3px rgba(0, 0, 0, 0.25);
    }

    .title {
        font-family: 'Teko', sans-serif;
        font-size: 36px;
        color: #555;
    }

    .radio-url:link, .radio-url:visited {
        font-family: 'Teko', sans-serif;
        font-size: 18px;
        text-decoration: none;
        color: #84C2C0;
        border-bottom: 2px solid #84C2C0;
    }

    .fas {
        font-size: 16px;
        margin-left: 5px;
    }

    audio {
        margin-top: 40px;
        width: 80%;
    }
</style>