<template>
  <div class="auth-container">
    <h2>Login</h2>
    <form @submit.prevent="login" class="auth-form">
      <label for="email">Email</label>
      <input type="email" id="email" v-model="email" required />

      <label for="password">Password</label>
      <input type="password" id="password" v-model="password" required />

      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
import { ref } from "vue";
import { supabase } from "../supabase";
import router from "../router";

export default {
  setup() {
    const email = ref("");
    const password = ref("");

    async function login() {
      try {
        const { data, error } = await supabase.auth.signInWithPassword({
          email: email.value,
          password: password.value,
        });

        if (error) {
          console.error("Error logging in:", error.message);
        } else {
          console.log("User logged in:", data);
          router.push("/user-dashboard");
        }
      } catch (error) {
        console.error("Error logging in:", error.message);
      }
    }

    return { email, password, login };
  },
};
</script>

<style scoped>
body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  background-color: #f4f1de;
}

.auth-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-image: url('https://www.transparenttextures.com/patterns/diagmonds-light.png');
}

h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: #4b4b4b;
}

.auth-form {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

label {
  font-size: 1rem;
}

input {
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #4b4b4b;
  border-radius: 5px;
}

button {
  padding: 0.5rem 1rem;
  font-size: 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  background-color: #264653;
  color: #ffffff;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #1d3557;
}
</style>
