<template>
  <div>
    <h1>Events</h1>

    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import EventCard from '@/components/EventCard.vue'

export default {
  // References to Vue components used in this page
  components: {
    EventCard
  },

  // Life cycle hook provided by Nuxt. It loads beofre page components, calls api and automatically integrates with computed properties
  async fetch({ store, error }) {
    try {
      await store.dispatch('events/fetchEvents')
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time. Please try again'
      })
    }
  },

  // Computed properties gets state data from mapState (Vuex Store)
  computed: mapState({ events: (state) => state.events.events }),

  // property used by vue-meta to add header tags
  head() {
    return {
      // The title of the webpage
      title: 'Event Listing'
    }
  }
}
</script>

<style lang="scss" scoped></style>
