<template>
  <Navbar />
  <div v-for="(idol, i) in idols" :key="i">
    <figure>
      <img :src="idol.src" alt="프사">
      </figure>
    <h3 class="infoTitle" :style="idol.fontColor">{{ idol.title }}</h3>
    <p>사장: {{ idol.owner }}</p>
    <p>회사: {{ idol.company }}</p>
    <span>좋아요 수: {{idol.like }} -</span>
    <button @click="increseLike(idol)">좋아요</button>
    <p>
      <button @click="handleModal(i);">상세보기</button>
    </p>
  </div>

  <Modal :idols="idols" :isModal="isModal" :selected="selected" :handleModal="handleModal"/>
</template>

<script>
import datas from "./assets/idols.js";
import Navbar from "./components/Navbar.vue";
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  data() {
   return {
    isModal: false,
    idols:datas,
    selected:0
  }
  },
  methods: {
    increseLike(idol){
      idol.like++;
    },

    handleModal(i){
      this.isModal = !this.isModal;
      this.selected = i;
    }
  },
  components:{
    Navbar: Navbar,
    Modal: Modal
  }

}
</script>

<style>
.infoTitle{
  background-color: yellow;
}

</style>
