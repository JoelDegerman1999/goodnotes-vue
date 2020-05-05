<template>
  <section>
    <NavigationBar @addPostit="alertMe"/>
    <Postit/>
  </section>
</template>

<script>
import NavigationBar from './NavigationBar'
import Postit from './Postit'

export default {
components: {
    Postit: Postit,
    NavigationBar: NavigationBar
  
  },
  data() {
    return {
      hej: 'hej'
    }
  },
  methods: {
    alertMe() {
      alert(this.hej)
    }
  }
}
</script>

<style>

</style>