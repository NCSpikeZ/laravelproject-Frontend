<template lang="pug">
LoginForm
</template>

<script>
export default({
  name: 'IndexPage',
  methods: {
      goToDashboard() {
        this.$router.push('/dashboard');
      },
    },
}