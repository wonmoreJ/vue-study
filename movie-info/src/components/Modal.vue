<template>
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>Detail</h3>
      <p>{{ idols[selected].title }}</p>
      <button @click="handleModal">닫기</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "ModalComponent",
  props: {
    idols: Array,
    isModal: Boolean,
    selected: Number,
    handleModal: Function,
  },
};
</script>
<style>
.modal {
  background-color: rgba(0, 0, 0, 0.7);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner {
  background-color: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>
