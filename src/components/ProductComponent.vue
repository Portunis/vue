<template>
  <!-- eslint-disable-next-line vue/max-attributes-per-line -->
  <div class="cart">
    <p>User is premium: {{ premium }}</p>
    <p>Cart({{ cart }})</p>
    <button v-if="cart >= 1" @click="clearToCart">Удалить один товар </button>
    <button v-if="cart >= 1"  @click="clearAllCart">Очистить корзину </button>
  </div>

  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img :src="image" alt="image">
        <p v-if="inStock">In Stock</p>
        <p v-else :class="{ textdecor: !inStock}">Out of Stock</p>
        <p>Shipping: {{ shipping }}</p>
      </div>
      <div class="product-info">
        <h1>{{ title }}</h1>
        <div class="textcols">
          <div class="textcols-item">
            <h2>Color</h2>
            <div
              class="color-box"
              v-for="(variant, index) in variants"
              :key="variant.id"
              :style="{ backgroundColor:variant.color }"
              @mouseover="updateProduct(index)"
            ></div>
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
        <button v-if="inSale"
                @click="addToCart"
                :disabled="!inStock"
                :class="{ disabledButton: !inStock }"
        >
          Купить со скидкой {{ sale }}
        </button>
        <button v-else @click="addToCart" :disabled="!inStock">Add to cart</button><br><br>
        <span :href="link">More products like this</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductComponent',
  components: {
  },
  data() {
    return {
      details: ['50% cotton', '30% wool', '20% polyester'],
      sizes: ['S', 'M', 'L', 'XL'],
      product: 'Socks',
      brand: 'Vue Mastery ',
      description: 'A pair of warm fuzzy socks',
      image: 'https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg',
      altText: 'A pair of socks',
      link: 'https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks',
      inStock: true,
      inSale: false,
      sale: '50%',
      variants: [
        {
          id: 2234,
          color: 'green',
          image: 'https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg',
          quantity: 10,
        },
        {
          id: 2235,
          color: 'blue',
          image: 'https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg',
          quantity: 0,
        },
      ],
      selectedVariant: 0,
      cart: 0,
      premium: true,
    };
  },
  methods: {
    addToCart() {
      this.cart += 1;
    },
    clearToCart() {
      this.cart -= 1;
    },
    clearAllCart() {
      this.cart = 0;
    },
    updateProduct(index) {
      this.selectedVariant = index;
      console.log(index);
    },
  },
  computed: {
    title() {
      return `${this.brand} ${this.product}`;
    },

  },

};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
