<template>
    <div class="logout">
      <h2>You have been logged out</h2>
      <button @click="goToLogin">Go to Login</button>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  import { useRouter } from 'vue-router';
  
  export default defineComponent({
    name: 'UserLogout',
    setup() {
      const router = useRouter();
  
      const logout = () => {
        localStorage.removeItem('authenticated');
        router.push('/login');
      };
  
      const goToLogin = () => {
        router.push('/login');
      };
  
      logout();
  
      return {
        goToLogin,
      };
    },
  });
  </script>
  
  <style scoped>
  .logout {
    max-width: 300px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 4px;
    text-align: center;
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
  </style>