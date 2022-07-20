<template>
  <div>
    <img class="roomImg" :src="dummydata.image" />
    <h4 class="title" @click="$emit('openModal')">{{ dummydata.title }}</h4>
    <p>{{ dummydata.price }}</p>
  </div>
</template>
<script>
export default {
  name: "ItemList",

  props: {
    dummydata: Object,
  },
  methods: {},
};
</script>
<style>
.title {
  cursor: pointer;
}
</style>
