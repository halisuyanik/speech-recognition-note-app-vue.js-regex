<template>
  <div id="app">
    <app-header></app-header>
    <div id="appContainer">
      <speech :addNote="addNote" :deleteNote="deleteNote" :removeAllNotes="removeAllNotes"/>
      <note-item v-for="note in notes" :key="note.id" :noteItem="note"></note-item>
    </div>
  </div>
</template>



<script>
import appHeader from "@/components/appHeader";
import noteItem from "@/components/noteItem";
import speech from "@/components/speech";

export default {
  components: {
    appHeader,
    noteItem,
    speech
  },

  data(){
    return{
      notes:[
        {id:1, note:"note1"},
        {id:2, note:"note2"},
        {id:3, note:"note3"},
        {id:4, note:"note4"},
    ]
    };  
  },
  methods: {
    addNote(note) {
      this.notes.push({
        id: this.notes.length + 1,
        note: note
      });
    },
    deleteNote(id) {
      this.notes.splice(
        this.notes.findIndex(n => n.id == id),
        1
      );
    },
    removeAllNotes() {
      this.notes = [];
    }
  }
};
</script>

