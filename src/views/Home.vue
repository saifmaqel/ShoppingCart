<template>
  <div class="home">
    <div class="container">
      <ProductDescriptionDrawer
      :product="product"
      :active="active.product_drawer"
      v-on:close-product-drawer="closeProductDrawer()"/>

      <div class="product-cards-container">
      <ProductSummaryCard 
      v-for="product in items"
      :key="product.id"
      :product="product"
      v-on:view-product="viewProduct($event)"/>
    </div>  
    </div>
  </div>
</template>

<script>
import items from '../data/items.js'
import ProductSummaryCard from '../components/products/ProductSummaryCard'
import ProductDescriptionDrawer from "../components/products/ProductDescriptionDrawer"
export default {
  name: 'Home',
  components: {
    ProductSummaryCard,
    ProductDescriptionDrawer
  },
  data(){
    return{
      items:items,
      product:null,
      active:{
        product_drawer:false
      }
    }
  },
  methods:{
    viewProduct(product){
      this.product = product 
      this.active.product_drawer = true
    },
    closeProductDrawer(){
      this.active.product_drawer = false
    }
  }
  
}
</script>

<style lang="scss">
.product-cards-container{
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-row-gap: 20px;
  grid-column-gap:30px;
  margin: 60px auto 0;
  width:85%;
  // margin: 60px 30px 0;
}
</style>
