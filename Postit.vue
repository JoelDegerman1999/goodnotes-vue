<template>
  <article class="postit">
    <div class="title">
      <h2 contenteditable v-text="rubrik" @blur="onEditTitle">{{rubrik}}</h2>
    </div>
    <hr>
    <div class="todo">
      <p contenteditable v-text="todoInfo" @blur="onEditInfo">{{todoInfo}}</p>
    </div>
  </article>
</template>

<script>
export default {
  props: {

  },
  data() {
    return {
      rubrik: "Hello",
      todoInfo: 'placeholder'
    };
  },
  methods: {
    onEditInfo(e) {
      this.todoInfo = e.target.innerText
    },
    onEditTitle(e) {
      this.rubrik = e.target.innerText
    }
  }
};
</script>

<style scoped>
.postit {
  box-sizing: border-box;
  width: 250px;
  height: 350px;
  background: rgb(255, 239, 90);
  padding: 1rem;
}

hr{
  border: 0.2px solid black;
  margin-bottom: 0.2rem;
}
</style>