<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button'
}
</script>

<style scoped>
.btn {
  padding: 10px 15px;
  margin-top: 10px;
  background: black;
  text-align: center;
  width: 200px;
  color: white;
  font-style: oblique;
  font-size: 16px;
  border: 1px solid teal;
  border-radius: 10px;
}
.btn:hover {
    cursor: pointer; 
    border: 2px solid #FD6E07;
}
</style>
