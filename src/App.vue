<template>
  <div id="app" class="container-fluid">
    <div class="row">
      <app-search v-on:newsChanged="getNews">
      </app-search>
    </div>
     <div>
        <label for="title">title</label>
        <input type="radio" id="title" value="title"
        v-model="sortCriteria">    
        <br>
         <div>
        <label for="author">author</label>
        <input type="radio" id="author" value="author"
        v-model="sortCriteria">    
    </div>
    </div>
    <div class="row">
      <app-articles v-for="newsArticle in sortedArticles"
      v-bind:data="newsArticle">
      </app-articles>
    </div>
  </div>
</template>
<!-- --------------------------------------------- -->
<script>
// import HelloWorld from './components/HelloWorld.vue'
import Articles from './components/Articles.vue';
import Search from './components/Search.vue';
export default {
  data: function() {
    return {
      articles: [],
      searchQ: 'politics',
      sortCriteria: ''
    }
  },
  methods: {
    getNews: function(query) {
      var that = this;
      var url = 'https://newsapi.org/v2/everything?' + 'q=' + query + '&' + 'apiKey=089c75fbc1fe40c6816196c43ba55d3e';
      var req = new Request(url);
        fetch(req)
        .then(function(response) {
            return response.json();
        })
        .then(function(data) {
            console.log(data)
            that.articles = data.articles;
        })
        this.searchQ = '';
        this.sortCriteria = '';
    },
    sortBy: function(arr, sortCrit) {
      return arr.sort(function(a, b){
        if (a[sortCrit] > b[sortCrit]) return 1;
        if (a[sortCrit] < b[sortCrit]) return -1;
        return 0;
      });
    }
  },
  computed: {
    sortedArticles: function() {
      if (this.sortCriteria){
      return this.sortBy(this.articles, this.sortCriteria);
    }
      return this.articles;
    }
  },
  components: {
    'app-articles': Articles,
    'app-search': Search
  },
  mounted: function() {
    this.getNews(this.searchQ);
  },
}
</script>
<!-- ------------------------------------------ -->
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
