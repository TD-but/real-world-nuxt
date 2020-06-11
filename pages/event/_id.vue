<template>
  <div>
    <h1>Event #{{ this.$route.params.id }}</h1>
  </div>
</template>

<script>
export default {
  computed: {
    id() {
      return this.$route.params.id
    }
  },
  // property used by vue-meta to add header tags
  head() {
    return {
      // The title of the webpage
      title: 'Event #' + this.id,

      // Array of meta tags to be used in the webpage header
      meta: [
        // A description meta tag
        {
          hid: 'description',
          name: 'description',
          content: 'What you need to know about event #' + this.id
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped></style>
