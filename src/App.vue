<template>
  <div class="blockBg" v-if="modalState == true">
    <div class="whiteBg">
      <button @click="modalState = false">X</button>
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="menuName in menuNames" :key="menuName">{{ menuName }}</a>
  </div>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <div>
    <h4>{{ products[0] }} 원룸</h4>
    <p>50 만원</p>
    <button @Click="increase()">허위매물신고</button>
    <span>신고횟수 : {{ reportCount[0] }}</span>
  </div>
  <div>
    <h4>{{ products[1] }} 원룸</h4>
    <p>70 만원</p>
    <button @Click="increase()">허위매물신고</button>
    <span>신고횟수 : {{ reportCount[1] }}</span>
  </div>
  <div>
    <h4>{{ products[2] }} 원룸</h4>
    <p>70 만원</p>
    <button @Click="increase()">허위매물신고</button>
    <span>신고횟수 : {{ reportCount[2] }}</span>
  </div> -->
  <div v-for="(some, i) in products" :key="i">
    <img class="roomImg" :src="require(`./assets/room${i}.jpg`)" />
    <h4 @click="modalState = true">{{ some }} 원룸</h4>
    <p>{{ prices[i] }}</p>
    <button @Click="reportCount[i]++">허위매물신고</button>
    <span>신고횟수 : {{ reportCount[i] }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      modalState: false,
      reportCount: [0, 0, 0],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      menuNames: ["HOME", "SHOP", "ABOUT"],
      prices: [50, 40, 70],
    };
  },

  components: {},
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

.blockBg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.whiteBg {
  width: 100%;
  background-color: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
