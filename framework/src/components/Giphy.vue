<template>
  <div>
    <md-toolbar class="md-primary">
      <label> Giphy Website - Quenteam 19.7 </label>
    </md-toolbar>
      <md-field class="wrapper">
        <md-input type="text" placeholder="Search..." id="search" v-model="query" v-on:input="getGiphy"></md-input>
      </md-field>
      <h2 v-if="query">Giphys for {{ query }}:</h2>
      <div class="result md-layout md-gutter">
        <div v-for="(erg, index) in apiResult" class="gifWrapper md-layout-item md-size-30">
          <giph :url="erg.embed_url"></giph>
          <br v-if="(index+1)%3 == 0">
        </div>
      </div>
  </div>
</template>

<script>
  import axios from 'axios';
import Giph from './Giph.vue'

    export default {
      name: 'giphy',
      props: {
      },
    components: {
        Giph,
    },
      data () {
          return {
            apiResult: "",
            query: "",
          }
      },
      methods: {
        getGiphy(){
          axios.get("https://api.giphy.com/v1/gifs/search?q="+this.query+"&api_key=EFjHp6suVZINAuAJkhBpMZ8UXkGhAsx1&limit=12")
          .then(response => {
            this.apiResult = response.data.data;
            // console.log(response.data.data[0]);
            // console.log(this.query);
          })
        },
      },
    }

    
</script>

<style>
  .wrapper{
    position: relative;
    display: flex;
    min-width: 100px;
  }

  .result{
    /*display: flex;
    flex-direction: row;*/
  }

  #search {
    border: 1px solid grey;
    border-radius: 5px;
    height: 20px;
    width: 100%;
    padding: 2px 23px 2px 30px;
    outline: 0;
    background-color: #f5f5f5;
  }

  #search:hover, #search:focus {
    border: 1.5px solid #009688;
    background-color: white;
  }

  .gifWrapper {
    margin: 10px;
  }

body {
  background: #eee;
}
</style>
