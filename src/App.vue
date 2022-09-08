<template>
  <div id="nav">
    <router-link to="/" :class="{active: $route.name === 'Home'}">Home</router-link> |
    <router-link to="/cart" :class="{active: $route.name === 'Cart'}">Cart</router-link>
  </div>
  <router-view/>
</template>
<script>
export default {
  name:"App",
  mounted() {
    this.$store.commit('updateCartFromLocalStorage')
  }
}
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2b4d6e;
}
html, body{
  margin:0;
  padding:0;
  overflow-x: hidden;
}
body{
  background-color: rgb(245, 245, 245);
}
#nav{
  padding: 10px;
  width: 100%;
  height: 30px;
  background-color: white;
  line-height: 30px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  a{
    font-weight: bold;
    color:darkgray;
    text-decoration: none;
    margin:0 5px 0 5px;
    font-size: 1.25rem;

    &.active{
      color: #2c3e50;
    }
  }
}
.text-center{
  text-align: center;
}
.container{
  padding-left: 15px;
  padding-right: 15px;
  margin-right: auto;
  margin-left: auto;
}
@media (min-width: 768px) {
  .container {
    width: 750px;
  }
}

@media (min-width: 992px) {
  .container {
    width: 970px;
  }
}

@media (min-width: 1200px) {
  .container {
    width: 1170;
  }
}

</style>
