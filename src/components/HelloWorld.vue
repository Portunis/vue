<template>
  <div class="product">
    <div class="product-image"></div>
    <div class="product-info">
      <h1>{{ product }}</h1>
      <p>{{ description }}</p>
      <img :src="image" >
    </div>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  components: {
  },
  data() {
    return {
      product: 'Socks',
      description: 'A pair of warm fuzzy socks',
      image: 'https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg',
    };
  },
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
  img{
    width: 200px;
    height: 200px;
  }
</style>
