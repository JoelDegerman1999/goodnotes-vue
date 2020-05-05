<template>
  <section>
    <Header/>
    <Main/>
  </section>
</template>

<script>
import Header from './Header'
import Main from './Main'
// import Footer from './Footer'

export default {
  components: {
    Header: Header,
    Main: Main,
    // Footer: Footer
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');

  * {
    font-family: 'Montserrat', sans-serif;
    margin: 0;
    padding: 0;
  }

  body {
    padding: 0 1rem;
  }
</style>