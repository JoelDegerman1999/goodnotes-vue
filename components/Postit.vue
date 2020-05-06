<template>
  <div class="container">
    <article
      :class="{hidden: hideNote}"
      class="postit"
      v-for="(note,index) in noteList"
      :key="index"
      :style="note.myStyle"
    >
      <div class="title">
        <h2 contenteditable @blur="changeTitle($event, index)">{{note.title}}</h2>
        <div class="edit-div">
          <img src="../img/palette-24px.svg" class="palette-icon" @click="changeColor(index)">
          <img src="../img/delete-24px.svg" class="delete-icon" @click="deleteNote(index)" />
        </div>
      </div>
      <hr />
      <div class="content">
        <p contenteditable @blur="changeContent($event, index)">{{note.content}}</p>
      </div>
      <div class="todo">
        <div class="task">
        </div>
      </div>
    </article>
  </div>
</template>

<script>


function randomNum(min, max) {
  return Math.floor(Math.random() * (max - min + 1) + min);
}

export default {
  props: {
    noteList: Array,
    hideNote: Boolean,
    noteColors: Array
  },
  data() {
    return {
      changeNoteColors: this.noteColors[0]
    };
  },
  methods: {
    changeTitle(event, index) {
      this.noteList[index].title = event.target.innerText;
    },
    changeContent(event, index) {
      console.log(event.target)
      console.log(event.target.innerText)
      this.noteList[index].content = event.target.innerText;
    },
    deleteNote(index) {
      this.noteList.splice(index, 1);
    },
    changeColor(index) {
      let randNum = randomNum(0, this.changeNoteColors.length -1)
      this.noteList[index].myStyle.backgroundColor = this.changeNoteColors[randNum]
    }
  },
  computed: {
    
  }
};
</script>

<style scoped>
.hidden {
  display: none;
}

.edit-div {
  display: flex;
}

.postit {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  background: rgb(255, 239, 90);
  padding: 1rem;
  border-radius: 5px;

  box-shadow: 3px 3px 8px 0px rgba(0, 0, 0, 0.2);
}

.title {
  display: flex;
  justify-content: space-between;
}

h2 {
  width: 290px;
}

hr {
  border: 0.2px solid black;
  margin: 0.2rem 0 0.5rem 0;
}

.container {
  display: grid;
  grid-template-columns: repeat(4, 350px);
  grid-auto-rows: 450px;
  gap: 1.5rem;
}

.content {
  overflow: auto;
  line-height: 1.6rem;
}

.content p {
  height: 300px;
}

.delete-icon {
  cursor: pointer;
}
.palette-icon {
  cursor: pointer;
}
</style>