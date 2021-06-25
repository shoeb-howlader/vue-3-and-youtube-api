<template>
<div class="container">

  <SearchBar @termChange="onTermChange"/>
  <div class="row">
  <videoDetail :video="selectedVideo"/>
  <videoList :videos="videos" @videoSelect="onVideoSelect"/>
  </div>
</div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import axios from 'axios'
import VideoList from './components/videoList.vue';
import VideoDetail from './components/videoDetail.vue';
const API_KEY=process.env.VUE_APP_YOUTUBE_API_KEY;

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
    
  },
  data()
  {
    //var test=[];
    return { videos: [] , selectedVideo:null}
  },
  methods:{
    onTermChange(SearchTerm){
      console.log(process.env.VUE_APP_YOUTUBE_API_KEY)
      axios.get('https://www.googleapis.com/youtube/v3/search',{
      params:{
        key:API_KEY,
        type:'video',
        part:'snippet',
        q:SearchTerm
        
      }
      },
      {
        Headers:{
          'access-control-allow-origin':'http://localhost:8080/'
        }
      }
      
      ).then(response=>{this.videos=response.data.items
      })
      .catch(err => { if(err.request){ console.log(err.request) } if(err.response){ console.log(err.response) } });
    },
    onVideoSelect(video)
    {
      this.selectedVideo=video;
    }
  }
}
</script>

<style>
#appp {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
