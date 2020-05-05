<template>
  <section>
    <h1>Goodnotes</h1>
    <div class="addNote">
      <input type="text" v-model="input"/>
      <button @click="addPostit">Add note</button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      input: ''
    }
  },

  methods: {
    addPostit() {
      this.$emit('addPostit', this.input)
    }
  }
};
</script>

<style scoped>
section {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h1 {
  margin: 0;
  padding: 0;
  font-size: 3rem;
}
</style>