<template>
  <main>
    <AddPost @addPostit="addNote" @hideNote="hideNoteFunc"/>
    <Postit :noteList="postits" :hideNote="hideNote" :noteColors="noteColors"/>
  </main>
</template>

<script>
import AddPost from './AddPost'
import Postit from './Postit'

export default {
components: {
    Postit: Postit,
    AddPost: AddPost
  },
  data() {
    return {
      postits: [],
      noteColors: [],
      hideNote: false
    }
  },
  methods: {
    addNote(value) {
      this.postits.push(value.note)
      console.log(value)
      this.noteColors.push(value.noteColors)
    },
    hideNoteFunc() {
      this.hideNote = !this.hideNote
    }
  }
}
</script>

<style scoped>
</style>
