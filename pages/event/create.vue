<template>
  <div>
    <h1>Create an Event</h1>
  </div>
</template>

<script>
export default {
  // property used by vue-meta to add header tags
  head() {
    return {
      // The title of the webpage
      title: 'Create an Event',

      // Array of meta tags to be used in the webpage header
      meta: [
        // A description meta tag
        {
          hid: 'description',
          name: 'description',
          content: 'You can create a new event in your neighborhood'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped></style>
