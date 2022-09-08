<template>
  <div class="cart-payment-card">
      <div class="payment-card">
          <h3>Cart Total Cost: ${{cart_total}}</h3>
          <button class="view-product-button">Pay by Credit Card</button>
      </div>
  </div>
</template>

<script>
export default {
    name: "CartPaymentCard",
    props:['products'],
    computed: {
        cart_total(){
            return this.$store.getters.cartTotal  
        }
    }

}
</script>

<style lang="scss">
.cart-payment-card .view-product-button{
    border: 1px gray solid;
    padding:5px;
    background-color:rgb(69, 160, 187);
    color:white;
    cursor: pointer;  
    border-radius: 2px;
    height: 30px;
    transition: height .1s;
    &:hover{
        height: 35px;
    }
}
</style>