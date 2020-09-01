<template>
  <div id="app">
    <Header v-on:search-video="searchVideo($event)" :totalResult='totalResult'/>
    <div class="content-wrapper">
      <SearchResult :searchResult='searchResult' />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';

import Header from './components/Header.vue';
import SearchResult from './components/SearchResults.vue';

export default {
  name: 'App',
  components: {
    Header,
    SearchResult,
  },
  data() {
    return {
      searchResult: [],
      totalResult: [],
      nextPageToken: '',
      searchTerm: '',
    };
  },
  methods: {
    searchVideo(searchText) {
      const url = `https://www.googleapis.com/youtube/v3/search?&q=${searchText}&maxResults=50&part=snippet&key=AIzaSyCkRzTFaAnJQXBmwAP2sONMINlCIRSYpe4`;
      const config = {
        // headers: {
        //   'Content-Type': 'application/json',
        //   'Access-Control-Allow-Origin': '*',
        // },
      };
      console.log('hello-test');

      axios.get(url, config).then((res) => {
        this.searchResult = res.data.items;
        this.totalResult = res.data.pageInfo.totalResults;
        this.nextPageToken = res.data.nextPageToken;
      })
        .catch((error) => { console.log(error); });
    },
    loadMore(searchText) {
      const urlNext = `https://www.googleapis.com/youtube/v3/search?&q=${searchText}
      &maxResults=50&nextPageToken=${this.nextPageToken}
      &part=snippet&&key=AIzaSyCkRzTFaAnJQXBmwAP2sONMINlCIRSYpe4`;

      console.log('hello-test');
      axios.get(urlNext).then((res) => {
        this.searchResult = [...this.searchResult, res.data.items];
        this.nextPageToken = res.data.nextPageToken;
      })
        .catch((error) => {
          console.log(error);
        });
    },
  },

  created() {
    window.onscroll = () => {
      if (document.documentElement.scrollTop
      + window.innerHeight === document.documentElement.offsetHeight) {
        this.loadMore();
      }
    };
  },

};
</script>
