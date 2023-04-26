<template>
  <div class="cart">
    <h2>Cart</h2>
    <ul>
      <li v-for="item in cartItems" :key="item.id">{{ item.title }} - ${{ item.price }}</li>
    </ul>
    <p>Total: ${{ total }}</p>
    <button class="checkout-button" @click="checkout" :disabled="cartItems.length === 0">Checkout</button>
  </div>
</template>

<script>
export default {
  props: {
    cartItems: {
      type: Array,
      required: true,
    },
  },
  computed: {
    total() {
      return this.cartItems.reduce((acc, item) => acc + item.price, 0);
    },
  },
  methods: {
    checkout() {
      alert("Proceed to the checkout process");
      // Handle the checkout process here
    },
  },
};
</script>

<style scoped>
.cart {
  margin-top: 2rem;
  padding: 1rem;
  background-color: #f5f5f5;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.checkout-button {
  background-color: #28a745;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 0.5rem 1rem;
  cursor: pointer;
  transition: background-color 0.2s;
}

.checkout-button:hover {
  background-color: #218838;
}

.checkout-button:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}
</style>