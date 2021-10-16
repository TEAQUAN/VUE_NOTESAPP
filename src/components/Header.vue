<template>
  <header>
    <h1>NOTESAPP</h1>
    <div class="col-12">
      <Button />
    </div>
  </header>
</template>
<script>
import Button from "./Button";
export default {
  name: "Header",
  components: {
    Button,
  },
};
</script>
<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
