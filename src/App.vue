<template>
  <div class="home">
    <input type="text" v-model="keyword" />
    <button @click="add">住所自動入力</button>
    <p>Address：{{ show }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      keyword: "",
      show: "",
      apiKey: "OXeaE3yV5GOSKP8k3CJt6VuSF2ecvRA7IP34FZV",
    };
  },
  methods: {
    add() {
      axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.keyword}?apiKey=OXeaE3yV5GOSKP8k3CJt6VuSF2ecvRA7IP34FZV`).then((res) => {
        this.show = res.data[0].allAddress;
      });
    },
  },
};
</script>
