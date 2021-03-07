<template>
  <div class="container">
    Hello world
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import firstPersonGql from '~/apollo/queries/firstPerson.graphql';
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
        query: firstPersonGql,
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
