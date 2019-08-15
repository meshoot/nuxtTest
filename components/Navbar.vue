<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">Nuxt SSR</a>

    <div class="collapse navbar-collapse" >
      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <nuxt-link to="/" exact no-prefetch active-class="active" class="nav-link">
            Home
          </nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link to="/about" active-class="active" class="nav-link">
            About
          </nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link to="/users" active-class="active" class="nav-link">
            Users
          </nuxt-link>
        </li>
        <li class="nav-item" v-if="!hasToken">
          <nuxt-link to="/login" active-class="active" class="nav-link">
            Login
          </nuxt-link>
        </li>
        <li class="nav-item" v-else>
          <a @click.prevent="logout" active-class="active" class="nav-link">
            Logout
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  computed: {
    hasToken() {
      return this.$store.getters.hasToken
    }
  },
  methods: {
    logout() {
      this.$store.dispatch('logout')
      this.$router.push('/login')
    }
  }
}
</script>

