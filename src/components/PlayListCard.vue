<template>
  <div class="card">
      <a class="card-body" :href="'https://www.youtube.com/watch?v=' + video.id.playlistId" target="_blank">
          <div class="thumbnail">
              <div class="card-media playlist">
                <img class="card-media-img" :src="video.snippet.thumbnails.medium.url">
                  <div class="overlay-wrapper">
                      <div class="overlay"></div>
                      <p class="counter">37</p>
                    <svg viewBox="0 0 24 24" preserveAspectRatio="xMidYMid meet" focusable="false"
                    class="style-scope yt-icon"
                    style="pointer-events: none; display: block; width: 100%; height: 100%;">
                        <g class="style-scope yt-icon">
                            <path d="M3.67 8.67h14V11h-14V8.67zm0-4.67h14v2.33h-14V4zm0
                            9.33H13v2.34H3.67v-2.34zm11.66
                            0v7l5.84-3.5-5.84-3.5z" class="style-scope yt-icon"></path>
                        </g></svg>
                  </div>
              </div>
          </div>
          <div class="card-body-inner">
              <div id="title-meta">
                <a><h2 class="title">{{video.snippet.title}}</h2></a>
                    <div class="meta-info">
                    <span class="meta channel">{{video.snippet.channelTitle}}</span>
                </div>

              </div>
              <ul class="playlist-items text">
                  <li>{{video.snippet.description}}</li>
              </ul>

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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import '../scss/mixins.scss';

.card-media{
    // background-image: url('../assets/sponge.jpg');
    // background-position: center;
    // background-repeat:no-repeat;
    &.playlist{
        .overlay-wrapper{
            width:100px !important;
            height:100%;
            position:absolute;
            @include display-flex(column,center,center);
            z-index:12;
            right:0;
            .overlay{
                opacity:0.6 !important;
                right:0;
                z-index:-10
            }
            .counter{
                color:#fff;
                font-size:24px;
                margin-bottom:8px;

            }
            svg{
                width:55px !important;
                height:55px !important;
                fill:#fff;
                @media screen and (max-width:991.98px){
                    width:35px;
                    height:35px;
                }
            }
        }
    }
}

</style>
