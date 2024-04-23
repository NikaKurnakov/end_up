<template>
  <div class="dialog" v-if="show" @click.stop="hideDialog">
    <div @click.stop class="dialog__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>

export default {
  name: 'my-dialog',
  props: {
        show: {
            type: Boolean,
            default: false
        }
  },
  methods: {
      hideDialog() {
          this.$emit('update:show', false)
      }
  },
  mounted() {
      console.log('dialog mounted')
  }
}
</script>

<style scoped>
.dialog {
  z-index: 9999;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  display: flex;
}

.dialog__content {
  margin: auto;
  /* margin-left: 300px; */
  background: rgba(27, 33, 31, 0.9); 
  background: center url(../../../public/img/bg_cemetery.png) fixed;
  background-size: cover;
  color: white;
  border-radius: 12px;
  border: solid 1px #FD6E07;
  min-height: 50px;
  min-width: 300px;
  width: 60%;
  max-width: 600px;
  padding: 10px;
}
</style>
