<template>
    <form @submit.prevent="recoverPassword">
      <input v-model="email" type="email" placeholder="Email">
      <button type="submit">Recover Password</button>
    </form>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        email: ''
      };
    },
    methods: {
      async recoverPassword() {
        try {
          const response = await axios.post('/api/forgot-password', {
            email: this.email
          });
        } catch (error) {
        }
      }
    }
  };
  </script>
  
  <style scoped>
  </style>
  