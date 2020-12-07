<template>
    <div class="hello">
        <div class="product">
          <div class="image">
            <img :src="'/images/products/'+product.image" width="100%">
          </div>
          <div class="product-info">
            <h1>{{product.name}}</h1>
              <p>a great description about this product. The feature color is {{product.color}}</p>
              <h2>{{product.price}}</h2>
              <button class="auto" v-on:click="AddToCart(product)">Add to Cart</button>
          </div>
        </div>
        <a style="cursor: pointer; text-decoration: underline" v-on:click="navigate()">back</a>
    </div>
</template>

<script>
    import router from '../router'

    export default {
        name: 'Product',
        data () {
            return {
                id: 0,
                msg: ''
            }
        },
        created() {
            this.id = this.$route.params.id;
        },
        methods: {
            navigate() {
                router.go(-1);
            },
            AddToCart(item) {
              this.$root.$data.cart.push(item);
            },
        },
        computed: {
          product() {
            return this.$root.$data.products[this.id - 1];
          }
        }
    }
</script>

<style scoped>
    h1, h2 {
        font-weight: normal;
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

    .product {
      display: flex;
      flex-direction: horizontal;
    }

    .image {
      margin-right: 15px;
    }

    button {
      height: 50px;
      background: #000;
      color: white;
      border: none;
      border-radius: 10px;
    }


</style>
