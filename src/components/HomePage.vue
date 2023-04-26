<template>
  <div class="home-page">
    <h1>Tarot Reading</h1>
    <div class="actions">
      <button @click="goToLogin">Login</button>
      <button @click="goToSignup">Sign Up</button>
      <button @click="goToTarotCards">View Tarot Cards</button>
    </div>
  </div>
</template>

<script>
import { useRouter } from "vue-router";

export default {
  setup() {
    const router = useRouter();

    function goToLogin() {
      router.push("/login");
    }

    function goToSignup() {
      router.push("/signup");
    }

    function goToTarotCards() {
      router.push("/tarot-cards");
    }

    return { goToLogin, goToSignup, goToTarotCards };
  },
};
</script>

<style scoped>
body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  background-color: #f4f1de;
}

.home-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-image: url('https://www.transparenttextures.com/patterns/diagmonds-light.png');
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: #4b4b4b;
}

.actions {
  display: flex;
  gap: 1rem;
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
