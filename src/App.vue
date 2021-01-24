<template>
  <div id="app">
    <div>
      <span>post code:</span>
      <input type="text" v-model="postCode">
    </div>
    <div>
      <span>address:</span>
      <button @click="sarchAddress">住所検索</button>
      <span>{{address}}</span>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      postCode: "",
      address: "",
    };
  },
  methods: {
    async sarchAddress() {
      const addressData = await axios.get(`https://apis.postcode-jp.com/api/v3/postcodes/${this.postCode}?apiKey=sZUYVEO3ikDRfy4lihL95FXIZoS46dFsleGo5BA`);
      this.address = addressData.data.allAddress;
    },
  },
}
</script>

<style>
  #app div {
    margin: 15px;
  }

  input,
  button {
    margin: 0 10px;
  }
</style>
