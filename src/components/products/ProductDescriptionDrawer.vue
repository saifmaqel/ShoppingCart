<template>
  <div class="drawer-background" :class="{show: active}" >
      <div class="container"> 
          <div class="drawer" :class="{show: active}">
              <div class="drawer-close" @click="$emit('close-product-drawer')">
                  X
              </div>
              <div class="product-details" v-if="product">
                  <h3 class="text-center">{{product.name}} </h3>
                  <p class="text-center">{{product.description}} </p>
                  <h3 class="text-center">${{product.price.toFixed(2)}}</h3>
                  <div class="cart-total" v-show="product_total">
                      <h3>In Cart</h3>
                      <h4> {{product_total}} </h4>
                  </div>
                  <div class="button-container">
                      <button class="add" @click="addToCart()">Add</button>
                      <button  class="remove" @click="removeFromCart()">Remove</button>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
 name:"ProductDescriptionDrawer",
 props:['product', 'active'],
 methods:{
     addToCart(){
         this.$store.commit('addToCart', this.product)
     },
     removeFromCart(){
         this.$store.commit('removeFromCart', this.product)
     }
 },
 computed:{
     product_total(){
         return this.$store.getters.productQuantity(this.product)
     }
     
 }
}
</script>

<style lang="scss">
.drawer-background{
    width: 100%;
    height: 100vh;
    position: fixed;
    left: 0;
    top: 0;
    background-color: rgba(124,124,124, 0.55);
    z-index: 100;
    display: none;
    transition: display 0.5s;

    &.show{
        display: block;
    }
}
.drawer{
    height: 100vh;
    background-color: white;
    position: fixed;
    top:0;
    left:-105vw;
    padding: 15px;
    transition: left 6s;
    z-index: 101;
    overflow-y: scroll;
    &.show{
        left:0vw;
    }
}
@media (min-width: 330px) {
  .drawer {
    width: 220px;
  }
}

@media (min-width: 768px) {
  .drawer {
    width: 320px;
  }
}

@media (min-width: 992px) {
  .drawer {
    width: 330px;
  }
}

@media (min-width: 1200px) {
  .drawer {
    width: 350px;
  }
}

.drawer-close{
    font-size:1.3rem;
    padding: 3px;
    border-radius: 5px;
    // right: 10px;
    text-align: center;
    border: 2px solid rgb(87, 87, 87);
    color:rgb(66, 66, 66);
    width: 15px;
    float: right;
    cursor: pointer;

    &:hover{
        background-color: rgb(255, 68, 78);        
    }
}
.product-details{
    display: flex;
    justify-content: center;
    flex-direction: column;
    p.description{
        padding: 20px;
        line-height: 1.5rem;
    }
}
.button-container{
    display: flex;
    justify-content:space-evenly;   
    button{
        width: 80px;
        border: none;
        padding: 10px;
        border-radius: 5px;
        // margin: 0 auto  10px auto;
        cursor:pointer;
         
    }
}
@media (max-width: 260px) {
    .button-container{
        justify-content: space-between;
        // margin: 0 auto;
        button{
            font-size: 13px;
            width: 65px;
        }
    }    
}
</style>