<template>
  <div class="card">
        <div class="card-content">
            <h3>{{ product.name }}</h3>
            <hr>
            <h5 class="price">Price: ${{ product.price.toFixed(2) }}</h5>
            <p class="description"><span>Description:</span> {{ description }}</p>
            <button class="view-product-button" @click="$emit('view-product',product)">View Product</button>
      </div>
  </div>
</template>

<script>
export default {
  name: "ProductSummaryCard",
  props: ["product"],
  computed:{
      description(){
          return this.product.description.substring(0, 150)
      }
  }
};
</script>

<style lang="scss">

.card-content {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    padding:30px;
    background-color:white;
    border-radius:10px;
  }
  .price{
      color: rgb(187, 20, 54);
      font-weight:20px;
  }
  p.description{
      color: rgb(5, 102, 134);
      font-weight:15px;
     line-height: 19px;
  }
  p.description span{
      font-weight:bolder;
      font-size: 17px;
  }
  .card-content button{
    border: 1px white solid;
    padding:5px;
    background-color:rgb(69, 160, 187);
    color:white;
    cursor: pointer;  
    border-radius: 2px;
  }
</style>