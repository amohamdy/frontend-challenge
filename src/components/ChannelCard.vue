<template>
  <div class="card">
      <a class="card-body" :href="'https://www.youtube.com/' + video.snippet.title">
          <div class="thumbnail">
            <div class="card-media channel">
                <img class="card-media-img" :src="video.snippet.thumbnails.medium.url"
                alt="YouTube thumbnail">
            </div>
          </div>
          <div class="card-body-inner">
              <div id="title-meta">
                <a><h2 class="title">{{video.snippet.channelTitle}}</h2></a>
                <div class="meta-info">
                    <span class="meta subscribers">3857 subscribers</span>
                </div>
              </div>
              <p class="text">{{video.snippet.description}}</p>
          </div>

      </a>
  </div>
</template>

<script>

export default {
  name: 'ChannelCard',
  props: ['video'],
};
</script>

<style scoped lang="scss">
.card-media{

    &.channel{
        border-radius: 50%;
        width:200px;
        height:200px !important;
        margin:0 auto;
        @media screen and (max-width:991.98px){
            width:160px;
            height:160px !important;
        }
        img{
            border-radius: 50%;
        }
    }
}

</style>
