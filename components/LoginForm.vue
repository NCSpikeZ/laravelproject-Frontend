<template>
    <form @submit.prevent="login">
      <input v-model="email" type="email" placeholder="Email">
      <input v-model="password" type="password" placeholder="Password">
      <button type="submit">Login</button>
    </form>
  </template>
  
<script>  
export default {
  data() {
    return {
      email: '',
      password: ''
    };
  },
  methods: {
    async login() {
      try {
        console.log('Tentative de connexion...');
        const response = await this.$axios.post('/dashboard', {
          email: this.email,
          password: this.password
        });
        console.log(response);
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>