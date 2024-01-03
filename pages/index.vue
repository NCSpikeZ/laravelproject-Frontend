<template lang="pug">
LoginForm
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  methods: {
      goToDashboard() {
        this.$router.push('/dashboard');
      },
    },
}