<template>
  <div class="home">
    <input type="text" maxlength="7" v-model="postcode">
    <button @click="showAddress">住所自動入力</button>
    <p>Address:{{address}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      postcode: "",
      address: "",
    };
  },
  methods: {
      async showAddress() {
        let home = await axios.get (`https://apis.postcode-jp.com/api/v4/postcodes/${this.postcode}?apiKey=fkoKwxJ6aPRpr6GvKQvrRQEsP8TOFEaF3o7bwaa`
        );
        this.address=home.data;
        const HomeAddress = this.address[0].allAddress;
        this.address = HomeAddress;
      },
  }
};
</script>
