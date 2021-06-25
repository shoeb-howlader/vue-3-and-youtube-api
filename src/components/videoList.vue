<template lang="">
    <div class=" col">
        <ul class="list-group ">
            <videoListItem v-for="video in videos" :key="video.etag" :video="video" @videoSelect="videoSelect"/>
        </ul>
    </div>
</template>
<script>
import VideoListItem from './videoListItem.vue'
export default {
    components: { VideoListItem },
  name:'videoList' ,
  props:{
      videos:[]
  },
  methods:
  {
      videoSelect(video)
      {
          this.$emit('videoSelect',video)
      }
  }

}
</script>
<style >
    
</style>