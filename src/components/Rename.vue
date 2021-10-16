<template>
  <div :key="note.id" v-for="note in notes" class="task">
    <Note      @edit-note="$emit('edit-note', note)" 
     @delete-note="$emit('delete-note', note)"      :note="note" />
 </div>
</template>
<script>
import "bootstrap/dist/css/bootstrap.min.css";
import Note from "./Note";
export default {
  name: "Notes",
  props: {
    notes: Array,
  },
  components: {
    Note,
  },
  emits: ['delete-note'],
  //emits: ['edit-note'],

     
};
</script>
<style scoped>
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
</style>
