<template>
    <form ref="passwordResetForm" @submit.prevent="submitForm">
      <input v-model="passwordResetPayload.mail" type="email" placeholder="Email">
      <input v-model="passwordResetPayload.password" type="password" placeholder="New password">
      <input v-model="passwordResetPayload.password_confirmation" type="password" placeholder="Confirm new password">

      <nuxt-link to="/">Cancel</nuxt-link>
      <button type="submit">Confirm</button>
    </form>
  </template>
  
  <script>
  const passwordResetDefaultPayload = {
    password: null,
    password_confirmation: null,
    email: null,
  }
  
  export default {
    name: 'PasswordResetForm',
    data() {
      return {
        passwordResetPayload: Object.assign({}, passwordResetDefaultPayload),
      }
    },
    created() {
      this.passwordResetPayload.email = this.email
    },
    methods: {
      submitForm() {
        this.$refs.passwordResetForm.validate(async (valid) => {
          if (!valid) return
          this.isSubmitLoading = true
          try {
            await this.$axios.$post('auth/password/reset/', {
              ...this.passwordResetPayload,
              token: this.token,
            })
            this.$message.success('you-can-now-login-to-your-account')
            this.$to(this.localePath({ name: 'login' }))
          } catch (e) {
            this.$message.error(e)
          }
          this.isSubmitLoading = false
        })
      },
    },
  }
  </script>