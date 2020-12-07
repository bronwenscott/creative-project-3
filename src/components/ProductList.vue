<template>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="product in products" :key="product.id">
      <div class="info">
        <h1>{{product.name}}</h1>
      </div>
      <router-link :to="{ name: 'Product', params: {id: product.id}}">
        <div class="image">
          <img :src="'/images/products/'+product.image">
        </div>
      </router-link>
      <div class="price">
        <h2>{{product.price}}</h2>
        <button class="auto" v-on:click="AddToCart(product)">Quick Add</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'ProductList',
  props: {
    products: Array
  },
  methods: {
    AddToCart(item) {
      this.$root.$data.cart.push(item);
    },
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.product img {
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #D3D3D3;
  color: #000;
  padding: 10px 30px;
  margin-bottom: 5px;
  border-radius: 10px;
  height: 60px;
}

.info h1 {
  font-size: 16px;
  vertical-align: middle;
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
