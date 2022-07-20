<template>
  <transition name="fade">
    <Modal @closeModal="modalState = false" :dummydata="dummydata" :modalState="modalState" :titleNum="titleNum" />
  </transition>
  <div class="menu">
    <a v-for="menuName in menuNames" :key="menuName">{{ menuName }}</a>
  </div>

  <Discount></Discount>
  <button @click="normalSort()">기본값 정렬</button>
  <button @click="priceSort()">가격순 정렬</button>
  <button @click="nameSort()">이름순 정렬</button>
  <ItemList
    @openModal="
      modalState = true;
      titleNum = dummydata[i].id;
    "
    :dummydata="dummydata[i]"
    v-for="(el, i) in dummydata"
    :key="el"
  />
</template>

<script>
import data from "./data";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import ItemList from "./ItemList.vue";
export default {
  name: "App",
  data() {
    return {
      menuNames: ["HOME", "SHOP", "ABOUT"],
      dummydata: data,
      modalState: false,
      titleNum: 0,
    };
  },
  methods: {
    increse() {
      // this.dummydata[i].reportCount++;
    },
    priceSort() {
      this.dummydata.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    normalSort() {
      this.dummydata.sort(function (a, b) {
        return a.id - b.id;
      });
    },
    nameSort() {
      this.dummydata.sort(function (a, b) {
        if (a.title < b.title) return -1;
        if (a.title > b.title) return 1;
        return 0;
      });
    },
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    ItemList: ItemList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0;
}
div {
  box-sizing: border-box;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.roomImg {
  width: 100%;
  margin-top: 40px;
}
</style>
