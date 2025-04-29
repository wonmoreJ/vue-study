<template>
  <Navbar />
  <Event text="상단 이벤트 bar" />
  <SearchBar :idols="idol_temp" @searchMovie="searchMovie" />
  <p>
    <button @click="allSearchMovie">전체보기</button>
  </p>
  <Idols
    :idols="idol_temp"
    :increseLike="increseLike"
    :handleModal="handleModal"
    @emitTest="emitTest"
  />
  <Modal
    :idols="idols"
    :isModal="isModal"
    :selected="selected"
    :handleModal="handleModal"
  />
</template>

<script>
import datas from "./assets/idols.js";
import Navbar from "./components/Navbar.vue";
import Modal from "./components/Modal.vue";
import Idols from "./components/Idols.vue";
import Event from "./components/Event.vue";
import SearchBar from "./components/SearchBar.vue";
export default {
  name: "App",
  data() {
    return {
      isModal: false,
      idols: datas,
      idol_temp: [...datas],
      selected: 0,
    };
  },
  methods: {
    increseLike(idol) {
      idol.like++;
    },

    handleModal(i) {
      this.isModal = !this.isModal;
      this.selected = i;
    },

    emitTest() {
      this.idols[0].like++;
    },

    searchMovie(title) {
      //첫번쨰 매개변수는 입력된값, 두번째는 이전값
      //제목에 데이터에 있는지 확인 데이터이름과 동일하게 적어주면됨\

      const idol = this.idols.filter((idol) => {
        return idol.title.includes(title);
      });
      if (idol.length == 0) {
        alert("자료없음");
      }
      this.idol_temp = idol;
    },
    allSearchMovie() {
      this.idol_temp = [...this.idols];
    },
  },
  components: {
    Navbar: Navbar,
    Modal: Modal,
    Idols: Idols,
    Event: Event,
    SearchBar: SearchBar,
  },
};
</script>

<style></style>
