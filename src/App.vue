// template can have only one root
<template>
  <div id="app">
    <!-- v-on: = @ -->
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail v-bind:video="selectedVideo" />
    <VideoList @videoSelect="onVideoSelect" v-bind:videoList="videos"/> 
    <!-- pass a prop to the child. videos is the name of the prop and videos is data from this component -->
    <!-- v-bind: if videos are updated, the child is rerendered -->
    <!-- {{videos.length}} -->
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/searchBar.vue';
import VideoList from './components/videoList';
import VideoDetail from './components/videoDetail';
const API_KEY = 'AIzaSyAgCpmzDnH5XX1fVpTi7VI9SrHrEBYPzkE';
// import TextField from './components/textField.vue';

export default {
//use name for debugging tools
//data, methods and computed go here
  name: 'app',
  components: {
    SearchBar: SearchBar,
    VideoList,
    VideoDetail 
    // TextField: TextField
  },
  data: function(){ //this is a vue component, not an instance. it's a function not an object
    return {
      //initialize our data
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    onTermChange(searchTerm){
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet', //what kind of info we want back
          q: searchTerm //what we are looking for
        }
      }).then(response =>{
        //update data 
        this.videos = response.data.items;
      })
    },
    onVideoSelect(video){
      this.selectedVideo = video;
    }
  }
}
</script>

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
