<template>
  <v-container fluid>
    <v-layout justify-center>
      <v-card>
        <v-card-text>
          <v-container>
            <form ref="form" @submit.prevent="onSignout">
              <v-layout justify-center mt-3>
                <p class="subheading">Are you sure?</p>
              </v-layout>
              <v-layout justify-center mt-3>
                <v-btn
                  :disabled="this.$store.getters.loading"
                  :loading="this.$store.getters.loading"
                  type="submit"
                  color="success"
                >
                  Sign out
                  <span slot="loader" class="custom-loader">
                    <v-icon light>refresh</v-icon>
                  </span>
                </v-btn>
              </v-layout>
            </form>
          </v-container>
        </v-card-text>
      </v-card>
    </v-layout>
  </v-container>
</template>
<style>
@import '@/assets/style/custom-loader.css';
</style>
<script>
export default {
  middleware: 'auth',
  layout: 'default',
  head: {
    title: 'SignIn page'
  },
  methods: {
    onSignout() {
      this.$store.dispatch('auth/signOut')
    }
  }
}
</script>
