<template>
<div id="app">
  <div id="menu">
    <div id="brand">
      <router-link to="/">
        <img src="/images/bron.jpeg">
      </router-link>
    </div>
    <div id="side">
      <router-link to="/browse">
        <div class="menu-item browse">
          <div class = "menu-image">
          <img src="/images/3lines.png">
          </div>
          <p>search</p>
        </div>
      </router-link>
      <router-link to="/cart">
        <div class="menu-item">
          <div class = "menu-image">
          <img src="/images/shoppingbag.png">
          </div>
          <p>my cart ({{numberOfItems}})</p>
        </div>
      </router-link>
    </div>
  </div>
  <router-view />
  <div class="github">
      <a href="https://github.com/bronwenscott/creative-project-3" class="btn btn-primary">GitHub</a>
    </div>
</div>

</template>

<script>
export default {
name: 'home',
data() {
  return {}
},
computed: {
  numberOfItems() {
    return this.$root.$data.cart.length
  }
  }
}
</script>


<style>

.github {
  text-align: center;
}

* {
  box-sizing: border-box;
}

body {
  margin: 50px 100px;

}

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "none brand side";
  margin-bottom: 50px;
}

#menu a {
  color: #B84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 200px;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: right;
}

#side img {
  width: 50px;
}

.menu-item {
  display: flex;
  flex-direction: column;
}

.menu-image {
  width: 20px;
}

.menu-item p {
  margin: 0px;
}

.browse {
  margin-right: 50px;
}
</style>
