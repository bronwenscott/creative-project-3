<template>
<div class = "page">
<h1>My Cart</h1>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="product in cart" :key="product.id">
      <div class="info">
        <h1>{{product.name}}</h1>
      </div>
      <div class="image">
        <img :src="'/images/products/'+product.image">
      </div>
      <div class="price">
        <h2>{{product.price}}</h2>
        <button class="auto" v-on:click="RemoveItem(product)">Remove</button>
      </div>
    </div>
  </div>
</div>
</div>
</template>

<script>
export default {
  name: "Cart",
  computed: {
    cart() {
      return this.$root.$data.cart;
    }
  },
  methods: {
    RemoveItem(product) {
      let index = this.$root.$data.cart.indexOf(product);
      this.$root.$data.cart.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.page {
text-align: center;
}


.wrapper {
  margin-left: 25%;
  margin-right: 25%;
  align-items: center;

}


.product {
  margin-top: 50px;
  text-align: left;
}

.product img {
  border: 2px solid #333;
  height: 100px;
  width: 100px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: left;
  margin-bottom: 5px;
}

.info {
  color: #000;
  padding: 30px 0px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.price {
  display: flex;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
  border-radius: 10px;
}

.auto {
  margin-left: auto;
}
</style>
