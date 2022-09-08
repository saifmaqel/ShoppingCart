<template>
  <div class="cart">
    <div class="container">
      <div class="cart-head">
        <h1>My Cart</h1>
        <h3>Total Cost : ${{ totalCostCart }}</h3>
      </div>
      <div class="payment">
        <div class="cart-payment">
          <CartPaymentCard :products="items" />
        </div>
      </div>
      <div class="card-item-cards">
        <CartItemCard
          v-for="product in items"
          :key="product.id"
          :product="product"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CartItemCard from "../components/products/CartItemCard";
import CartPaymentCard from "../components/products/CartPaymentCard";
export default {
  name: "Cart",
  components: {
    CartItemCard,
    CartPaymentCard,
  },
  computed: {
    items() {
      return this.$store.getters.cartItems;
    },
    totalCostCart() {
      let total = 0;
      this.$store.getters.cartItems.map((i) => {
        total += i.price * i.quantity;
      });
      return total;
    },
  },
};
</script>

<style lang="scss" scoped>
.cart {
  margin-top: 50px;
}
.card-item-cards {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-row-gap: 20px;
  grid-column-gap: 30px;
  width: 85%;
  margin: 30px auto;
}
.cart .cart-head{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
  .cart-head h3{
    margin-top: 30px;
  }
@media (max-width: 370px) {
  // .cart .cart-head {
  //   flex-direction: column;
  // }
  .cart-head h3{
    display: none;
  }
}

// @media (max-width:992px) {
//   .cart-head h1{
//     font-size: 25px;
//   }
//   .cart-head h3{
//     font-size: 19px;
//   }
// }

</style>
