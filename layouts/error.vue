<template>
  <v-app dark>
    <h1
      v-if="error.statusCode === 404"
      class="error"
    >
      {{ pageNotFound }}
    </h1>
    <h1
      v-else
      class="error"
    >
      {{ otherError }}
    </h1>
    <NuxtLink to="/">
      Home page
    </NuxtLink>
  </v-app>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred'
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  }
}
</script>

<style scoped>
.error {
  font-size: 20px;
}
</style>
