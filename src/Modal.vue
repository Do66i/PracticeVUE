<template>
  <div class="blockBg" v-if="modalState == true">
    <div class="whiteBg">
      <Discount />
      <button class="btn" @click="$emit('closeModal')">X</button>
      <img :src="dummydata[titleNum].image" class="roomImg" />
      <h4>{{ dummydata[titleNum].title }}</h4>
      <p>{{ dummydata[titleNum].content }}</p>
      <input type="number" v-model.number="month" />
      <p v-if="typeof month === 'number'">{{ month }}개월 입력함 {{ dummydata[titleNum].price * month }} 원</p>
      <p v-else-if="typeof month === 'string'">숫자를 입력해주세요 🦭</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "TheModal",
  data() {
    return {
      month: 1,
    };
  },
  props: {
    dummydata: Object,
    modalState: Boolean,
    titleNum: Number,
  },
  watch: {
    month(text) {
      if (text >= 13) {
        alert("12이하의 수만 입력가능합니다");
        this.month = 1;
      }
    },
  },
  methods: {
    // test: function (e) {
    //   console.log(e.target.value);
    //   this.month = e.target.value;
    // },
  },
};
</script>

<style>
.blockBg {
  width: 100%;
  height: 100%;
  background: transparent;
  position: fixed;
  padding: 20px;
}

.whiteBg {
  width: 100%;
  background-color: white;
  border-radius: 8px;
  padding: 20px;
}

.discount {
  background-color: #eee;
  padding: 40px;
  margin: 10px;
  border-radius: 5px;
}
.btn {
  background-color: transparent;
  border: none;
  font-size: 20px;
  cursor: pointer;
}
</style>
