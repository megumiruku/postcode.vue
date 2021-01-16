<template>
  <div class="home">
    <input type="text" maxlength="7" v-model="postcode">
    <button @click="created()">住所自動入力</button>
    <p>Adress:{{adress}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      postcode: "",
      adress: ""
    };
  },
  methods: {
      async created() {
        let home = await axios.get ('https://apis.postcode-jp.com/api/v3/postcodes?p=${this.postcode}&appid=fkoKwxJ6aPRpr6GvKQvrRQEsP8TOFEaF3o7bwaa'
        );
        this.data=home.data;
        this.adress=this.data.allAdress;
      },
  }
  
}
</script>
