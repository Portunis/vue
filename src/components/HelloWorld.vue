<template>
  <div class="nav-bar"></div>

  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img :src="image">

      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p>{{ description }}</p>
        <button :href="link">More products like this</button>

      </div>
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
      altText: 'A pair of socks',
      link: 'https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks',
    };
  },
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
