<template>
  <div class="nav-bar"></div>
  <div class="cart">
    <p>Cart({{ cart }})</p>
    <button v-if="cart >= 1" @click="delToCart">Удалить один товар </button>
    <button v-if="cart >= 1"  @click="delAllCart">Очистить корзину </button>
  </div>

  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img :src="image">
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <div class="textcols">
          <div class="textcols-item">
            <h2>Color</h2>
            <div v-for="variant in variants" :key="variant.id">
              <p @mouseover="updateProduct(variant.image)">
                {{ variant.color }}
              </p>
            </div>

          </div>
          <div class="textcols-item">
            <h2>Details</h2>
            <ul>
              <li v-for="detail in details" :key="detail.id">{{ detail }}</li>
            </ul>
          </div>
          <div class="textcols-item">
            <h2>Sizes</h2>
            <ul>
              <li v-for="size in sizes" :key="size.id">{{ size }}</li>
            </ul>
          </div>
        </div>
        <p>{{ description }}</p>
        <button v-if="inSale" @click="addToCart">Купить со скидкой {{ sale }} </button>
        <button v-else @click="addToCart">Add to cart</button>
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
      details: ['50% cotton', '30% wool', '20% polyester'],
      sizes: ['S', 'M', 'L', 'XL'],
      product: 'Socks',
      description: 'A pair of warm fuzzy socks',
      image: 'https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg',
      altText: 'A pair of socks',
      link: 'https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks',
      inStock: true,
      inSale: true,
      sale: '50%',
      variants: [
        {
          id: 2234,
          color: 'green',
          image: 'https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg',
        },
        {
          id: 2235,
          color: 'blue',
          image: 'https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg',
        },
      ],

      cart: 0,

    };
  },
  methods: {
    addToCart() {
      this.cart += 1;
    },
    delToCart() {
      this.cart -= 1;
    },
    delAllCart() {
      this.cart = 0;
    },
    updateProduct(variantImage) {
      this.image = variantImage;
    },
  },
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
