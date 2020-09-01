<template>
  <div class="card">
      <a class="card-body" :href="'https://www.youtube.com/watch?v=' + video.id.videoId" target="_blank">
        <div class="thumbnail">
            <div class="card-media">
                <img class="card-media-img" :src="video.snippet.thumbnails.medium.url"
                alt="YouTube thumbnail">
            </div>
        </div>
          <div class="card-body-inner">
              <div id="title-meta">
                <a><h2 class="title">{{video.snippet.title}}</h2></a>
                <div class="meta-info">
                    <a :href="'https://www.youtube.com/' + video.snippet.channelTitle"> <span class="meta channel">{{video.snippet.channelTitle}}</span></a>
                    <!-- <span class="meta views">26k views</span> -->
                    <span class="meta published">{{video.snippet.publishedAt}}</span>
                </div>
              </div>
              <p class="text">{{video.snippet.description}}</p>
          </div>

      </a>
  </div>
</template>
<script>
export default {
  name: 'VideoCard',
  props: ['video'],
};
</script>

<style scoped lang="scss">
    .card-body{
        h2{
            margin-top:0;
        }
    }

</style>
