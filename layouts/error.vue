//Template section for Vue file which contains the HTML elements
<template>
  <div>
    <!-- exclamantion mark svg  -->
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="90"
      height="90"
      fill="#DBE1EC"
      viewBox="0 0 48 48"
    >
      <path
        d="M22 30h4v4h-4zm0-16h4v12h-4zm1.99-10C12.94 4 4 12.95 4 24s8.94 20 19.99 20S44 35.05 44 24 35.04 4 23.99 4zM24 40c-8.84 0-16-7.16-16-16S15.16 8 24 8s16 7.16 16 16-7.16 16-16 16z"
      />
    </svg>

    <!-- Error message being displayed  -->
    <div class="title">
      {{ message }}
    </div>

    <!-- If the error code is page not found then show link to the home page -->
    <p v-if="statusCode === 404">
      <nuxt-link to="/">
        Return to homepage
      </nuxt-link>
    </p>
  </div>
</template>

//Contains all javascript elements for the vue component
<script>
export default {
  name: 'NuxtError',
  // data passed to component from outside
  props: {
    // Send in the error
    error: {
      type: Object,
      default: null
    }
  },

  // Computed properties cache results and only re-load when dependencies are changed
  computed: {
    statusCode() {
      return (this.error && this.error.statusCode) || 500
    },
    message() {
      return this.error.message
    }
  },

  // property used by vue-meta to add header tags
  head() {
    return {
      // The title of the webpage
      title: this.message
    }
  }
}
</script>
