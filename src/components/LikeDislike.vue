<template>
    <div class="social-wrapper">
        <div class="like-dislike">
            <button class="social-btn" id="like">
                <img src="../assets/like.svg">
                <span>7.2K</span>
            </button>
            <button class="social-btn" id="dislike">
                <img src="../assets/like.svg">
                <span>100</span>
            </button>
            <button class="social-btn" id="share">
                <img src="../assets/share.svg">
                <span>Share</span>
            </button>
            <button class="social-btn" id="dislike">
                <svg viewBox="0 0 24 24" preserveAspectRatio="xMidYMid meet" focusable="false"
                    class="style-scope yt-icon"
                    style="pointer-events: none; display: block; width: 100%; height: 100%;">
                    <g class="style-scope yt-icon">
                        <path d="M3.67 8.67h14V11h-14V8.67zm0-4.67h14v2.33h-14V4zm0
                        9.33H13v2.34H3.67v-2.34zm11.66
                        0v7l5.84-3.5-5.84-3.5z" class="style-scope yt-icon"></path>
                    </g></svg>

                <span>Save</span>
            </button>

        </div>

    </div>
</template>

<script>
export default {
  name: 'LikeDislike',
};
</script>

<style scoped lang="scss">
  @import '../scss/variables.scss';
  @import '../scss/mixins.scss';

.like-dislike{
    @include display-flex(row,flex-start,center);

    .social-btn{
        background-color:transparent !important;
        @include display-flex(row,flex-start,center);
        border:0;
        margin-right:12px;
        img,svg{
            fill:$text-gray;
            width:30px !important;
            height:30px !important;
            margin-right:8px;
        }
    }
    #dislike{
        img{
            transform:rotate(180deg);
            margin-top:8px;

        }
    }
    }

</style>
