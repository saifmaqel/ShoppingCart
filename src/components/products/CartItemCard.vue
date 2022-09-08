<template>
  <div class="card">
          <div class="card-content">
              <h2>{{product.name}}</h2>
              <hr>
              <h4> Product Price: ${{product.price}} </h4>
              <h4> Product Quantity: {{product.quantity}} </h4>
              <h4> Total Cost: ${{totalCost}} </h4>
              <p>{{description}}}</p>

      </div>
  </div>
</template>

<script>
export default {
    name:"CartItemCard",
    props:['product'],
    computed:{
        description(){
            return this.product.description.substring(0,120) 
        },
        totalCost(){
            return this.product.price * this.product.quantity 
        }
    }

}
</script>

<style>

</style>