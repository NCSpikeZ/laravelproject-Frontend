<template>
  <form @submit.prevent="updateProfile">
    <input v-model="name" type="text" placeholder="Name">
    <input v-model="email" type="email" placeholder="Email">
    <button type="submit">Update Profile</button>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        email: ''
      };
    },
    methods: {
      async updateProfile() {
        try {
          const response = await this.$axios.$put('/api/profile', {
            name: this.name,
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