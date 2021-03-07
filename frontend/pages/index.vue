<template>
  <div class="container">
    Hello world
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import ggl from 'graphql-tag'

export default Vue.extend({
  name: 'App',
  components: {

  },
  data () {
    return {
    }
  },
  async created() {
    await this.start()
  },
  computed: {

  },
  methods: {
    async start() {
      const result = await this.$apollo.query({
        query: ggl`
          query FirstPerson ($personID: ID!) {
            person(personID: $personID) {
              name
            }
          }
        `,
        variables: {
          personID: 1,
        }
      }).catch((err) => {
        console.error(err)
      })
      console.log(result);
    }
  }
})
</script>
