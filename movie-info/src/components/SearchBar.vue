<template>
  <div class="search-box">
    <input
      type="search"
      @change="
        $emit('searchMovie', $event.target.value);
        inputText = $event.target.value;
      "
    />
    <button>검색</button>
  </div>
  <p>{{ inputText }}</p>
</template>
<script>
export default {
  name: "SearchBarComponent",
  data() {
    return {
      inputText: "",
    };
  },
  props: {
    idols: Array,
  },
  watch: {
    inputText(name) {
      //첫번쨰 매개변수는 입력된값, 두번째는 이전값
      //제목에 데이터에 있는지 확인 데이터이름과 동일하게 적어주면됨
      const idol = this.idols.filter((idol) => {
        return idol.title.includes(name);
      });
      if (idol.length == 0) {
        alert("자료없음");
      }
    },
  },
};
</script>
<style>
.search-box {
  padding: 10px;
  display: flex;
  justify-content: center;
}

.search-box input {
  padding: 5px 10px;
}

.search-box button {
  margin: 0;
}
</style>
