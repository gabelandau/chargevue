<!--

filename: Purpose.vue
description: Tasks

author: Gabe Landau <gll1872@rit.edu>

-->

<template>
  <div class="description">
    <div class="columns">
      <div class="column">
        <div class="description_title">Purpose</div>
      </div>
      <div class="column">
        <div class="description_date">9/20/17</div>
      </div>
    </div>
    <div class="divider"></div>
    <div class="description_content">Students gender neutral bathrooms. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin feugiat pretium sem, id accumsan mauris consequat at. Nam dolor velit, efficitur id malesuada ac, sodales at ligula. Vivamus convallis enim id risus elementum, eget mattis ante hendrerit.</div>
  </div>
</template>

<script>
  export default {
    name: 'purpose',
    components: {},
    data () {
      return {
      }
    }
  }
</script>

<style scoped>
  .description {
    background-color: #fff;
    border: 1px solid #ddd;
    width: 70%;
    margin: 50px auto 0 auto;
  }

  .description_title {
    text-align: left;
    font-size: 18pt;
  }

  .description_date {
    text-align: right;
    font-size: 14pt;
    color: #555;
  }

  .description_content {
    font-size: 13pt;
    padding: 10px;
  }

  .columns {
    padding: 0;
    margin: 0;
  }

  .divider {
    border-top: 1px solid #000;
  }
</style>
