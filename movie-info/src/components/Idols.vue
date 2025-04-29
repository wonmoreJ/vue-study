<template>
  <div v-for="(idol, i) in idols" :key="i">
    <figure>
      <img :src="idol.src" alt="프사" />
    </figure>
    <h3 class="infoTitle" :style="idol.fontColor">{{ idol.title }}</h3>
    <p>사장: {{ idol.owner }}</p>
    <p>회사: {{ idol.company }}</p>
    <span>좋아요 수: {{ idol.like }} -</span>
    <button @click="increseLike(idol)">좋아요</button>
    <p>
      <button @click="handleModal(i)">상세보기</button>
    </p>
    <p>
      <button @click="$emit('emitTest')">emit 테스트</button>
    </p>
  </div>
</template>
<script>
export default {
  name: "IdolsComponent",
  props: {
    idols: Array,
    increseLike: Function,
    handleModal: Function,
  },
};
</script>
<style>
.infoTitle {
  background-color: yellow;
}
</style>
