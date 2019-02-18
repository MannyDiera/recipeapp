<template>
  <div class="modal-drop">
    <div class="modal-content">
      <button @click="close" class='modal-close'>&times;</button>
      <slot>default content</slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'simple-modal',
  methods: {
    close() { this.$emit('close-modal', this.recipe) }
  },
};
</script>

<style>
.modal-drop {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0,0,0);
  background-color: rgba(0,0,0,0.4);
}

.modal-content {
  position: relative;
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

.modal-close {
  position: absolute;
  top: 0;
  right: 0;
}
</style>
