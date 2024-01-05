<template>
    <form @submit.prevent="recoverPassword">
      <input v-model="email" type="email" placeholder="Email">
      <button type="submit">Recover Password</button>
    </form>
  </template>
  
<script>  
  export default {
    data() {
      return {
        email: ''
      };
    },
    methods: {
      async recoverPassword() {
        try {
          const response = await this.$axios.$post('/api/forgot-password', {
            email: this.email
          });
          console.log(response);
        } catch (error) {
          console.error(error);
        }
      }
    }
  };
</script>