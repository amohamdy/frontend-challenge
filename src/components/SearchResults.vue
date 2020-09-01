<template>
  <div id="search-result">
      <div class="search-result-wrapper">
        <div class="video-wrapper" v-for="video in searchResult" :key="video.etag">
          <VideoCard :video="video" v-if="video.id.kind.split('#')[1] == 'video'"/>
          <PlayListCard :video="video" v-else-if="video.id.kind.split('#')[1] == 'playlist'"/>
          <ChannelCard :video="video" v-else/>

        </div>
    </div>
  </div>
</template>

<script>
import VideoCard from './VideoCard.vue';
import ChannelCard from './ChannelCard.vue';
import PlayListCard from './PlayListCard.vue';

export default {
  name: 'SearchResult',
  props: ['searchResult', 'totalResult'],
  components: {
    VideoCard,
    PlayListCard,
    ChannelCard,

  },
};
</script>

<style scoped lang="scss">

  #search-result{
      padding-top:5rem;
      @media screen and (max-width:767.98px){
        padding:1.5rem;
      }

  }
</style>
