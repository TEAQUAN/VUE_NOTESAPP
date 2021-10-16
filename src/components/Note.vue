<template>
  <div  class="row">
     <h3> 
       {{ note.title }} 
       <button @click="OnDelete(note)" class="btn btn-danger">DELETE</button>
      <button @click="onEdit(note)" class="btn btn-secondary">EDIT</button>
     </h3> 
    <p>
      {{ note.content }}
      </p>
  </div>
</template>
<script>
 import {  useRouter } from 'vue-router'
export default {
  name: "Note",
  props: {
    note: Object,
  },
  setup(){
    // const route = useRoute()
     const router = useRouter()
    const onEdit = (id) => {
      console.log({id: id.title})
      router.push({path: "/Edit", query: {id: id.id,}})
    }
    return {
      onEdit
    }
  },
  methods: {
   OnEdit(id) {
     this.$emit("edit-note",id);
     console.log("black");
      },
    OnDelete(notes) {
      this.$emit("delete-note", notes);
    },
  },
};
</script>
