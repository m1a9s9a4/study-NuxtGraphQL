<template>
  <div class="container">
    Hello world
    {{person ? person.name : ''}}
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import firstPersonGql from '~/apollo/queries/firstPerson.graphql';

export default Vue.extend({
  name: 'App',
  data () {
    return {
      person: {},
    }
  },
  async created() {
    await this.start()
  },
  methods: {
    async start() {
      this.person = await this.$apollo.query({
        query: firstPersonGql,
        variables: {
          personID: 1,
        }
      }).then(({data}) => {
        return data.person ?? {}
      }).catch((err) => {
        console.log(err)
        return {}
      })
      console.log(this.person);
    }
  }
})
</script>
