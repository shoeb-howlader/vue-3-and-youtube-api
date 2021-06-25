<template lang="">
    <div v-if="video" class="col">
        <div class="ratio ratio-21x9">
            <iframe class="embed-responsive-item" :src="videoUrl" title="YouTube video player" ></iframe>
        </div>
        <div class="details">
        <h4>{{video.snippet.title}}</h4>
        <p>{{video.snippet.description}}</p>
        </div>
        
    </div>
</template>
<script>
export default {
   name:'videoDetail',
   props:['video'] ,
   computed:{
       videoUrl()
       {
           const videoId = this.video.id.videoId;
           //console.log(this.video.id.videoId)
          console.log(videoId)
           return 'https://www.youtube.com/embed/'+videoId
       }
   }
}
</script>
<style scoped>
   .details{
       margin-top: 10px;
       padding: 10px;
       border:1px solid #ddd;
       border-radius: 4px;
   } 
</style>