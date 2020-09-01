<template>
    <div class="video-detail">
            <div class="video-detail-inner">
                <div class="video-frame">
                    <iframe width="420" height="315"
                    src="https://www.youtube.com/embed/tgbNymZ7vqY">
                    </iframe>
                </div>
                <div class="video-frame-details">
                    <div class="top">
                        <div>
                            <h2>Poines on spongepop 4D</h2>
                            <span class="base">1700 watching now</span>
                        </div>
                        <LikeDislike/>
                    </div>
                    <div class="bottom">
                        <img class="avatar" src="../assets/avatar.png">
                        <div class="channel-info">
                            <h2>itsfortoo</h2>
                            <span class="base">Published on 21 Dec 2014</span>
                        </div>
                    </div>
                </div>
            </div>
            <div class="related-videos">
                <RelatedVideo/>
            </div>
        </div>
</template>

<script>
import RelatedVideo from './RelatedVideo.vue';
import LikeDislike from './LikeDislike.vue';

export default {
  name: 'VideoDetails',
  components: {
    RelatedVideo,
    LikeDislike,
  },
};
</script>

<style scoped lang="scss">
  @import '../scss/variables.scss';
  @import '../scss/mixins.scss';

.video-frame{
    iframe{
        width:100%;
        border:0;
    }
}
.video-frame-details{
    height:250px;
    @include display-flex(column,flex-start,flex-start);
    .top,.bottom{
        height:50%;
        width:100%;
        border-bottom:1px solid $border-gray;
        padding:10px;
    }
    .bottom{
        @include display-flex(row,flex-start,center);
        img{
            width:150px;
            height:150px;
            align-self: flex-start;
        }
    }
    .top{
        @include display-flex(row,space-between,center);

    }
}

</style>
