<template>
  <form ref="loginForm" @submit.prevent="handleSubmitForm">
    <input v-model="userPayload.email" type="email" placeholder="Email">
    <input v-model="userPayload.password" type="password" placeholder="Password">
    <button type="submit" :loading="isSubmitLoading">Login</button>
    <nuxt-link to="forgotpassword">Forgot password ?</nuxt-link>
  </form>
</template>

<script>
export default {
  name: 'LoginFormComponent',
  data() {
    return {
      userPayload: {
        email: '',
        password: ''
      },
      isSubmitLoading: false
    };
  },
  methods: {
    async handleSubmitForm() {
      try {
        console.log('Attempting login...');
        this.isSubmitLoading = true;

        const response = await this.$axios.post('/api/login', this.userPayload);

        if (response.status === 200) {
          console.log('Login successful:', response);

          this.$router.push('/dashboard');
        } else {
          throw new Error('Invalid status code');
        }
      } catch (error) {
        console.error('Login error:', error);
      } finally {
        this.isSubmitLoading = false;
      }
    }
  }
};
</script>
