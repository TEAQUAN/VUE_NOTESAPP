<template>
  <div class="container">
    <a class="labtn" href="/">Go Back</a>
    <form @submit.prevent="HandleSubmit" class="row g-3">
      <div class="col-12">
        <label for="title" class="form-label">Title</label>
        <input
          @change="changeinput()"
          id="title"
          v-model="notestitle"
          placeholder="INPUT TITLE"
          class="rabaranks"
          required
          type="text"
        />
      </div>

      <div class="col-12">
        <label for="description" class="form-label">Content</label>
        <textarea
          id="description"
          @change="changetext"
          v-model="notescontent"
          class="form-control"
          aria-label="With textarea"
          required
          placeholder="WRITE TEXT"
        ></textarea>
      </div>

      <div class="col-12">
        <input  type="submit" value="Save" class="success" />
      </div>
    </form>
  </div>
</template>
<script>
// import { computed, onMounted } from "vue"
import { useRoute } from "vue-router";
export default {
  name: "Edit",
  components: {},
  data() {
    return {
      notestitle: "",
      notescontent: "",
      notedisplay: {},
    };
  },
  methods: {
    changeteinput(e) {
      e.target.notestitle;
    },
    changetext(e) {
      e.target.notescontent;
    },
    HandleSubmit() {
      this.setup();
      console.log(this.notescontent, this.notestitle);
    },
    setup() {
      const route = useRoute();
      // onMounted(() => {
      //   const newId = route.query
      // })
      console.log("Hi There");

      let notes = [];
      let noted = {};
      var presentNotes = localStorage.getItem("notes");
      var deserialisedpresentNotes = JSON.parse(presentNotes);
      if (
        deserialisedpresentNotes != null &&
        deserialisedpresentNotes.length > 0
      ) {
        notes = deserialisedpresentNotes;
        console.log(notes);
        noted = notes.find((o) => o.id == route.query.id);
        console.log(noted);
        this.notestitle = noted.title;
        this.notescontent = noted.content;
      
      }
      console.log(route.query);
      return { newId: route.query.id };
    },
  },
  // beforeMount() {
  //   console.warn("before mount", this.$el);
  // },
  mounted() {
    this.setup();
    if (localStorage.getItem("notes")) {
      try {
        this.notestitle = JSON.parse("noted");
        console.log(this.notedisplay);
      } catch (e) {
        console.log(e)
      }
    }
  },
};
</script>
<style scoped>
.rabaranks {
  border-radius: 30px;
  size: 50;
  border-radius: 0 2em;
  padding: 0, 10px;
  width: 100%;
  line-height: 2em;
  margin-bottom: 20px;
}
</style>
<style>
.success {
  background-color: firebrick;
  padding: 5px;
  color: white;
  font-size: 15px;
  font-weight: bold;
  border: none;
  border-radius: 5px;
  padding-left: 10px;
  padding-right: 10px;
  margin-right: 5px;
}
.labtn {
  background-color: firebrick;
  padding: 5px;
  color: white;
  font-size: 15px;
  font-weight: bold;
  border: none;
  border-radius: 5px;
  padding-left: 10px;
  padding-right: 10px;
  margin-right: 5px;
}
</style>