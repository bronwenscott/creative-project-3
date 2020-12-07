<template>
<div>
  <div class="pure-menu pure-menu-horizontal">
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select('card')" href="#" class="pure-menu-link">card</a></li>
      <li class="pure-menu-item"><a @click="select('download')" href="#" class="pure-menu-link">download</a></li>
      <li class="pure-menu-item"><a @click="select('print')" href="#" class="pure-menu-link">print</a></li>
    </ul>
  </div>
  <div class="pure-menu pure-menu-horizontal">
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select_color('blue')" href="#" class="pure-menu-link">blue</a></li>
      <li class="pure-menu-item"><a @click="select_color('multi')" href="#" class="pure-menu-link">multi</a></li>
      <li class="pure-menu-item"><a @click="select_color('pink')" href="#" class="pure-menu-link">pink</a></li>
      <li class="pure-menu-item"><a @click="select_color('red')" href="#" class="pure-menu-link">red</a></li>
    </ul>
  </div>
  <ProductList :products="products" />
</div>
</template>

<script>
import ProductList from "../components/ProductList.vue"
export default {
  name: 'Browse',
  components: {
    ProductList
  },
  data() {
    return {
      type: '',
      color: ''
    }
  },
  computed: {
    products() {
      if (this.type === '' && this.color === '') {
        return this.$root.$data.products;
      }
      else if (this.type != '' && this.color === '') {
        return this.$root.$data.products.filter(product => product.type === this.type);
      }
      else if (this.type === '' && this.color != '') {
        return this.$root.$data.products.filter(product => product.color === this.color);
      }
      return this.$root.$data.products.filter(product => product.type === this.type);
      return this.$root.$data.products.filter(product => product.color === this.color);
    }
  },
  methods: {
    select(type) {
      this.type = type;
    },
    select_color(color) {
      this.color = color;
    }
  }
}
</script>
