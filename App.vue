<template>
  <section>
    <Main/>
  </section>
</template>

<script>
// import Header from './Header'
import Main from './components/Main'
// import Footer from './Footer'

export default {
  components: {
    // Header: Header,
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
    background-color: #fefefe;
    padding: 1rem 1rem 0;
    height: 100vh;
  }

  section {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    width: 100%;
    height: 100%;
  }
</style>