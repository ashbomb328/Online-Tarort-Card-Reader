<template>
  <div class="checkout">
    <h1>Checkout Page</h1>
    <div class="products">
      <div class="product" v-for="product in products" :key="product.id">
        <img :src="product.image" :alt="product.title" />
        <h2>{{ product.title }}</h2>
        <p>Price: ${{ product.price }}</p>
        <p>Category: {{ product.category }}</p>
        <p>{{ product.description }}</p>
        <button class="add-to-cart" @click="addToCart(product)">Add to Cart</button>
      </div>
    </div>
    <Cart :cartItems="cart" />
  </div>
</template>

<script>
import supabase from "../supabaseClient";
import Cart from "./Cart.vue";

export default {
  components: {
    Cart,
  },
  data() {
    return {
      products: [],
      cart: [],
    };
  },
  methods: {
    addToCart(product) {
      this.cart.push(product);
    },
  },
  async created() {
    try {
      const { data, error } = await supabase.from("product").select("*");
      if (error) {
        console.error("Error fetching products:", error);
      } else {
        this.products = data;
      }
    } catch (err) {
      console.error("Error fetching products:", err);
    }
  },
};
</script>

<style scoped>
.checkout {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
  font-family: Arial, sans-serif;
}

.products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1rem;
}

.product {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  background-color: #f5f5f5;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.add-to-cart {
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 0.5rem 1rem;
  margin-top: 1rem;
  cursor: pointer;
  transition: background-color 0.2s;
}

.add-to-cart:hover {
  background-color: #0056b3;
}

img {
  max-width: 100%;
  height: auto;
  object-fit: cover;
  border-radius: 4px;
  margin-bottom: 1rem;
}
</style>