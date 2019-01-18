<template>
  <div id="app">
    <Search v-on:SearchRequested="handleSearch"></Search>
    <p v-if="isLoading" style="text-align:center;">Yükleniyor...</p>
    <h2 class="title">{{title}}</h2>
    <p></p>
    <ListPage :gifs=gifs></ListPage>
  </div>
</template>

<script>
import styles from './assets/css/project.css'
import Search from './components/Search.vue'
import ListPage from './components/ListPage.vue'
export default {
  name: 'app',
  components: { Search, ListPage },
  data(){
    return {
      title: 'Gündemdekiler',
      ratings: 'G',
      language: 'en',
      limit: '12',
      isLoading: true,
      gifs: []
    }
  },
  methods: {
    queryStart(url){
      fetch(url)
      .then((res) => { return res.json()})
      .then((res) => {
        this.gifs = res.data;
        this.isLoading= false;
      })
    },
    handleSearch(query, limit, ratings, language){
      this.gifs= [];
      this.isLoading= true;
      const url= 'https://api.giphy.com/v1/gifs/search?api_key=wuG901dsm94iHrP02PJ1NVDZvzoNXdfB&q='+ query +'&limit='+ limit +'&offset=0&rating='+ ratings +'&lang='+ language +'';
      this.queryStart(url);
      this.title=query;
    }
  },
  created(){
    const url= 'https://api.giphy.com/v1/gifs/trending?api_key=wuG901dsm94iHrP02PJ1NVDZvzoNXdfB&limit='+ this.limit +'&offset=0&rating='+ this.ratings +'&lang='+ this.language +'';
    this.queryStart(url);
  }
}
</script>
