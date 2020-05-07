<template>
  <div class="home">
    <h1>{{ msg }}</h1>
    <p>{{ description }}</p>
    <p>{{ msg2 }}</p>
    <div class="product">
      <div class="product-image">
        <img :src="cardImage" :alt="selectedCard" />
        <img :src="cardIcon" :alt="selectedCardIcon" />
      </div>

      <div class="product-info">
        <h1>{{ product }}</h1>

        <p>{{ description }}</p>
        <ul>
          <li>{{ this.variants[this.selectedIndex].variantName }}</li>
          <li>{{ this.variants[this.selectedIndex].variantHodnota }}</li>
        </ul>
        <div
          v-for="(variant, index) in variants"
          :key="variant.variantID"
          class="color-box"
          :style="{ backgroundColor: variant.variantColor }"
          :title="variant.variantName"
          @mouseover="updateProduct(index)"
        >
          <button
            v-on:click="addToCart"
            :disabled="!variant.variantStatus"
            :class="{ disabledButton: !variant.variantStatus }"
          >
            <img :src="cardIcon" :alt="selectedCardIcon" />
          </button>
        </div>
        <div class="cart">
          <p>Cart({{ cart }})</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Karty',
  props: {
    msg: String,
    msg2: String
  },
  data() {
    return {
      product: 'karts',
      description: 'Sejměte kartu, karta s nejvyšší hodnotou vyhravá.',
      altText: 'Nejvyssi karta',
      link: 'https://www.talon.cz/',
      link2: 'https://www.vuemastery.com/',
      selectedCard: '',
      selectedCardIcon: '',
      selectedIndex: 0,
      variants: [
        {
          variantID: 0,
          variantName: 'srdcove',
          variantHodnota: 'eso',
          variantColor: 'red',
          variantImage: 'c_eso.jpg',
          variantIcon: 'srdce.png',
          variantStatus: false
        },
        {
          variantID: 1,
          variantName: 'listove',
          variantHodnota: 'eso',
          variantColor: 'green',
          variantImage: 'e_eso.jpg',
          variantIcon: 'listy.png',
          variantStatus: true
        },
        {
          variantID: 2,
          variantName: 'zaludove',
          variantHodnota: 'eso',
          variantColor: 'brown',
          variantImage: 'z_eso.jpg',
          variantIcon: 'zaludy.png',
          variantStatus: true
        },
        {
          variantID: 3,
          variantName: 'kulove',
          variantHodnota: 'eso',
          variantColor: 'blue',
          variantImage: 'k_eso.jpg',
          variantIcon: 'kule.png',
          variantStatus: true
        }
      ],
      cart: 0
    }
  },
  methods: {
    updateProduct(index) {
      this.selectedIndex = index
      console.log(index)
    },
    addToCart: function() {
      this.cart += 1
    }
  },
  computed: {
    cardImage() {
      return require(`../assets/${
        this.variants[this.selectedIndex].variantImage
      }`)
    },
    cardIcon() {
      return require(`../assets/${
        this.variants[this.selectedIndex].variantIcon
      }`)
    }
  }
}
</script>

<style scoped>
.nav-bar {
  background: linear-gradient(-90deg, #84cf6a, #16c0b0);
  height: 60px;
  margin-bottom: 15px;
}

.product {
  display: flex;
  flex-flow: wrap;
  padding: 1rem;
}

img {
  border: 1px solid #d8d8d8;
  width: 80%;
  margin: 0px;
  box-shadow: 0px 0.5px 1px #d8d8d8;
}

.product-image {
  width: 50%;
}

.product-image,
.product-info {
  margin-top: 10px;
  width: 20%;
  color: #282828;
  margin: 0px;
  text-align: left;
}

.color-box {
  width: 40px;
  height: 40px;
  margin-top: 5px;
}

.cart {
  margin-right: 25px;
  float: right;
  border: 1px solid #d8d8d8;
  padding: 5px 20px;
}

button {
  margin-top: 0px;
  border: none;
  /* background-color: #ffffff;*/
  background: rgba(100%, 70%, 100%, 0.1);
  color: white;
  height: 40px;
  width: 40px;
  font-size: 14px;
}

.disabledButton {
  background-color: #d8d8d8;
}

.review-form {
  width: 400px;
  padding: 20px;
  margin: 40px;
  border: 1px solid #d8d8d8;
}

input {
  width: 100%;
  height: 25px;
  margin-bottom: 20px;
}

textarea {
  width: 100%;
  height: 60px;
}

.tab {
  margin-left: 20px;
  cursor: pointer;
}

.activeTab {
  color: #16c0b0;
  text-decoration: underline;
}
</style>
