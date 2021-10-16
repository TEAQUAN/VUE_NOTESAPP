<template>
  <div>
    <!-- <button to="../pages/Home.vue" @click="addNote()" class="btn btn-info">
      ADDNOTE
    </button> -->
    <router-link class="btn btn-info" to="/addnote">ADDNOTE</router-link>
  </div>
</template>
<script>
export default {
  name: "Button",
  methods: {
    addNote() {},
  },
};
</script>

