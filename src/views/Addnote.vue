<template>
  <div class="container">
    <form @submit="onSubmit" class="row g-3">
      <div class="col-12">
        <label for="title" class="form-label">Title</label>
        <input id="title" v-model="title" placeholder="TITLE" class="rabaranks" required   type="text"/>
      </div>

      <div class="col-12">
        <label  for="description" class="form-label">Content</label>
        <textarea
        id="description"
          v-model="content"
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
export default {
  name: "Addnote",
  components:{
  },
  data() {
    return{
       title: "",
       content: "",
    }
  },
  methods: {
    onSubmit(e) {
        e.preventDefault();
        if(!this.title && !this.content) {
          alert("Please add a title and some content");
          return
        } else {
          const NewNote = {
            id: localStorage.getItem("id") && JSON.parse(localStorage.getItem("notes")).length > 0 ?
                parseInt(localStorage.getItem("id")) : 1,
            title: this.title,
            content: this.content
          }
          localStorage.setItem("id", NewNote.id + 1);
        let notes = [];
        var presentNotes = localStorage.getItem('notes');
        var deserialisedpresentNotes = JSON.parse(presentNotes);
        if(deserialisedpresentNotes != null && deserialisedpresentNotes.length !== 0){
          notes = deserialisedpresentNotes;
        }
        notes.push(NewNote);
        localStorage.setItem("notes",JSON.stringify(notes));
          this.title = "";
          this.content = "";
          this.$router.push("/");
        }
      
        
    }
  },
  
};
</script>
<style scoped>
.rabaranks{border-radius:30px; size:50;  border-radius: 0 2em;
    padding: 0, 10px;
    width: 100%;
    line-height: 2em;
    margin-bottom: 20px;
    
}
</style>
<style>
 .success{

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