<template>
  <div class="ms-2 me-auto">
    <Header  />
    <Rename @edit-note="editNote"  @delete-note="deleteNote" :notes="notes" />
  </div>

</template>

<script>
import Header from "../components/Header.vue";
import Rename from "../components/Rename.vue";
export default {
  name: "App",
  components: {
    Header,
    Rename,
    
  },
  data() {
    return {
      notes: [],
    };
  },
  created() {

    var result = localStorage.getItem('notes');
    var deserialisedResult = JSON.parse(result);
    this.notes = deserialisedResult;


    // this.notes = [
    //   {
    //     id: 1,
    //     title: "Manchester City Vs Norwich City 2 - 0",
    //     content:
    //       "Are you unemployed and desperately needs a business that will give you steady income on a daily basis? STOP and congratulate yourself for being opportuned to come across this post.head office in Lagos, South west Nigeria. Driven by a passion to make a propelling impact in the gaming industry with a vision to create great opportunities for it's partners, host communities and staff).",
    //   },
    //   {
    //     id: 2,
    //     title: " Ex-Military Governor, Tunji Olurin Is Dead (Photo)",
    //     content:
    //       "Are you unemployed and desperately needs a business that will give you steady income on a daily basis? STOP and congratulate yourself for being opportuned to come across this post.head office in Lagos, South west Nigeria. Driven by a passion to make a propelling impact in the gaming industry with a vision to create great opportunities for it's partners, host communities and staff).",
    //   },

    //   {
    //     id: 3,
    //     title:
    //       " Divorce: Paul Okoye’s Wife, Anita, Demands N7.8 Million Monthly ",
    //     content:
    //       "Are you unemployed and desperately needs a business that will give you steady income on a daily basis? STOP and congratulate yourself for being opportuned to come across this post.head office in Lagos, South west Nigeria. Driven by a passion to make a propelling impact in the gaming industry with a vision to create great opportunities for it's partners, host communities and staff).",
    //   },
    //   {
    //     id: 4,
    //     title:
    //       " BBNaija: My Brother Has Schizophrenia – Maria Breaks Down In Tears",
    //     content:
    //       "Are you unemployed and desperately needs a business that will give you steady income on a daily basis? STOP and congratulate yourself for being opportuned to come across this post.head office in Lagos, South west Nigeria. Driven by a passion to make a propelling impact in the gaming industry with a vision to create great opportunities for it's partners, host communities and staff).",
    //   },
    //   {
    //     id: 5,
    //     title:
    //       "Five Supercops Who Went From Hero To Villain Before Abba Kyari ",
    //     content:
    //       "Are you unemployed and desperately needs a business that will give you steady income on a daily basis? STOP and congratulate yourself for being opportuned to come across this post.head office in Lagos, South west Nigeria. Driven by a passion to make a propelling impact in the gaming industry with a vision to create great opportunities for it's partners, host communities and staff).",
    //   },
    // ],
    this.getNotes()
  },
  methods: {

    getNotes() {},
 deleteNote(note) {
      if (confirm("are you sure?"))
      document.createAttribute("name")
        // this.notes =localStorage.removeItem("notes");
        var newNotes = this.notes.filter((item) => item != note);
        console.log(newNotes);
        this.notes = newNotes;
        localStorage.setItem("notes",JSON.stringify(newNotes));
        console.log("NOTE HAS BEEN DELETED")

        console.log(note);
        console.log(newNotes)
    },
  },
  editNote(note){
    if (confirm("are you sure?"))
    console.log(note);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align:left;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  padding: 40px;
}
</style>

