<template>
  <section class="main-section">
    <article class="header">
      <h1>Goodnotes</h1>
      <div class="addNote">
        <label class="addPost">
          {{addOrClose}}
          <img src="../img/add_box-24px.svg" @click="showForm" class="create-icon" />
        </label>
      </div>
    </article>

    <section class="createpost-section" :class="{hidden: hideForm}">
      <form>
        <div class="title-div">
          <label>Title</label>
          <input type="text" name="title" v-model="note.title" />
        </div>
        <div class="content-div">
          <label>Content</label>
          <textarea name="content" id cols="50" rows="17" v-model="note.content"></textarea>
        </div>
        <img src="../img/post_add-24px.svg" class="post-icon" @click="addPostit" />
      </form>
      <article class="postit">
        <div class="title">
          <h2>{{note.title}}</h2>
          <div class="edit-div"></div>
        </div>
        <hr />
        <div class="todo">
          <p>{{note.content}}</p>
        </div>
      </article>
    </section>
  </section>
</template>

<script>
function randomNum(min, max) {
  return Math.floor(Math.random() * (max - min + 1) + min);
}

export default {
  data() {
    return {
      noteColors: ["#b67929", "#a3acb1", "#3c5b74", "#264b77", "#00243f"],
      note: {
        title: "",
        content: "",
        myStyle: {
          backgroundColor: ""
        }
      },
      hideForm: true,
      addOrClose: "Add"
    };
  },

  methods: {
    addPostit() {
      this.note.myStyle.backgroundColor = this.noteColors[
        randomNum(0, this.noteColors.length)
      ];
      this.$emit("addPostit", {note: this.note, noteColors: this.noteColors});
      this.$emit("hideNote");
      this.note = {
        title: "",
        content: "",
        myStyle: {
          backgroundColor: ""
        }
      };
      this.hideForm = true;
    },
    showForm() {
      if (this.addOrClose == "Add") this.addOrClose = "Close";
      else this.addOrClose = "Add";
      this.hideForm = !this.hideForm;
      this.$emit("hideNote");
    }
  }
};
</script>

<style scoped>
.postit {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  box-sizing: border-box;
  width: 350px;
  height: 450px;
  background: rgb(255, 239, 90);
  padding: 1rem;
  border-radius: 5px;

  margin-left: 2rem;

  box-shadow: 3px 3px 8px 0px rgba(0, 0, 0, 0.2);
}

.title {
  display: flex;
  width: 100%;
  justify-content: space-between;
}
.todo {
  overflow: auto;
  line-height: 1.6rem;
}

.todo p {
  max-height: 360px;
}

.createpost-section {
  transition: all 1s ease;
  display: flex;
  align-items: center;
}

/* helper class */
.hidden {
  display: none;
}

/* --------- */

.main-section {
  margin-bottom: 1.5rem;
  display: flex;
  align-items: center;
  flex-direction: column;
}

article.header {
  border-radius: 5px;
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

form {
  display: flex;
  justify-content: center;
  flex-direction: column;
}

.title-div {
  display: flex;
  flex-direction: column;
  margin: 1rem 0;
}

.title-div label {
  font-size: 1.4rem;
  font-weight: 600;
  margin: 0 auto 0.2rem;
}

.content-div {
  display: flex;
  flex-direction: column;
}

.content-div label {
  font-size: 1.4rem;
  font-weight: 600;
  margin: 0 auto 0.2rem;
}

.create-post {
  display: flex;
  justify-content: flex-end;
}

input {
  border: none;
  border-radius: 5px;
  box-shadow: 0px 0px 8px 0px rgba(0, 0, 0, 0.2);
  font-size: 1.3rem;
  text-align: center;
  padding: 0.5rem 0.5rem;
}

textarea {
  box-sizing: border-box;
  border: none;
  border-radius: 5px;
  box-shadow: 0px 0px 8px 0px rgba(0, 0, 0, 0.2);
  line-height: 1.6rem;
  font-size: 1.2rem;

  padding: 0.5rem 0.5rem 0;
}

hr {
  width: 100%;
}
h1 {
  margin: 0;
  padding: 0;
  font-size: 3rem;
}

.addPost {
  width: 80px;
  display: flex;
  align-items: center;
  justify-content: space-around;
}

input {
  height: 25px;
}

.create-icon {
  cursor: pointer;
  width: 50px;
}

.post-icon {
  position: relative;
  bottom: 50px;
  left: 91%;
  cursor: pointer;
  width: 50px;
}
</style>