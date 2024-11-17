<template>
  <div class="login">
    <h2>Login</h2>
    <form @submit.prevent="login">
      <div>
        <label for="username">Username:</label>
        <input type="text" v-model="username" required />
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" v-model="password" required />
      </div>
      <button type="submit">Login</button>
      <p v-if="error">{{ error }}</p>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import { useRouter } from 'vue-router';

export default defineComponent({
  name: 'UserLogin',
  setup() {
    const router = useRouter();
    const username = ref('');
    const password = ref('');
    const error = ref('');

    const credentials = [
      { username: 'user1', password: 'pass1' },
      { username: 'user2', password: 'pass2' },
      { username: 'user3', password: 'pass3' },
    ];

    const login = () => {
      const user = credentials.find(
        (cred) => cred.username === username.value && cred.password === password.value
      );
      if (user) {
        localStorage.setItem('authenticated', 'true');
        router.push('/stats');
      } else {
        error.value = 'Invalid username or password';
      }
    };

    return {
      username,
      password,
      error,
      login,
    };
  },
});
</script>

<style scoped>
.login {
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

label {
  display: block;
  margin-bottom: 8px;
}

input {
  width: 100%;
  padding: 8px;
  margin-bottom: 16px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #369f6e;
}

p {
  color: red;
}
</style>