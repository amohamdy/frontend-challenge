<template>
  <div class="sub-head">
      <div class="toolbar-search-result">
            <p class="search-result base" v-if="totalResult > 0">
                About {{totalResult}} result
            </p>
            <button class="filter-btn" @click.prevent="isToggle = !isToggle">
                <svg viewBox="0 0 24 24" preserveAspectRatio="xMidYMid meet"
                focusable="false"
                class="style-scope yt-icon"
                style="pointer-events: none; display: block; width: 100%; height: 100%;">
                <g class="style-scope yt-icon">
                <path d="M0 0h24v24H0z" fill="none" class="style-scope yt-icon"></path>
                <path d="M3 17v2h6v-2H3zM3 5v2h10V5H3zm10 16v-2h8v-2h-8v-2h-2v6h2zM7
                9v2H3v2h4v2h2V9H7zm14
                4v-2H11v2h10zm-6-4h2V7h4V5h-4V3h-2v6z"
                class="style-scope yt-icon"></path>
                </g></svg>
                <span class="base">Filter</span>
            </button>
      </div>
        <div class="filter-dropdown" v-if="isToggle">
            <div class="filter upload-date">
                <h3>UPLOAD DATE</h3>
                <ul class="filter-list">
                    <li class="base" v-for="item in uploadDate" :key="item.index">
                     <FilterItem :item="item"></FilterItem>
                     </li>
                </ul>
            </div>
             <div class="filter type">
                <h3>TYPE</h3>
                <ul class="filter-list">
                    <li class="base" v-for="item in type" :key="item.index">
                        <FilterItem :item="item"></FilterItem>

                     </li>
                </ul>

            </div>
            <div class="filter sort-by">
                <h3>SORTBY</h3>
                <ul class="filter-list">
                    <li class="base" v-for="item in
                    sortBy" :key="item.index">
                    <FilterItem :item="item"></FilterItem>

                    </li>
                </ul>

            </div>

        </div>
        <div class="filter-dropdown-responsive">
            <select name="type" id="type">
                <option selected value="">All</option>
                <option class="base" v-for="item in type" :key="item.index">{{item}}</option>
            </select>

            <select name="upload-date" id="upload-date">
                <option selected value="">Any Time</option>
                <option class="base" v-for="item in uploadDate" :key="item.index">{{item}}</option>
            </select>
        </div>
  </div>
</template>

<script>
import FilterItem from './FilterItem.vue';

export default {
  name: 'SubHeader',
  props: ['totalResult'],
  components: {
    FilterItem,
  },
  data() {
    return {
      isToggle: false,
      sortBy: ['Relevance', 'Upload Date', 'View Count', 'rating'],
      type: ['Video', 'Channel', 'Playlist'],
      uploadDate: ['Last Hour', 'Today', 'This Week', 'This Month'],
    };
  },
};
</script>

<style scoped lang="scss">
  @import '../scss/mixins.scss';
  @import '../scss/variables.scss';

.sub-head{
    padding:2rem 0;
    width:70%;
    margin:5rem auto 1.5rem;
    border-bottom:1px solid $border-gray;
    @media screen and (max-width:991.98px){
        padding:0;
        margin:1rem;
        width:92%;
    }

    @media screen and (min-width:992px) and (max-width:1199.98px){
        width:80%;
    }

    .toolbar-search-result{
        @include display-flex(row,space-between,center);
        @media screen and (max-width:991.98px){
            display:none;
        }
        .base{
            color:$text-gray;
            font-size:22px !important;
        }
        .filter-btn{
            @include display-flex(row, flex-start, center);
            margin-left:auto;
            border:0;
            background-color:#fff;
            svg{
                fill:$text-gray;
                width:30px !important;
                height:30px !important;
                margin-right:12px;
            }
        }
    }
    .filter-dropdown{
        @include display-flex(row, flex-start, flex-start);
        @media screen and (max-width:991.98px){
                display:none;
            }
        .filter{
            width:calc(100% / 3 - 2rem);
            margin:0 1rem;

            h3{
                border-bottom:1px solid $border-gray;
                padding:16px 0;
            }
            li{
                margin-bottom:16px;
            }
        }
    }
    .filter-dropdown-responsive{
        @media screen and (min-width:992px){
            display:none;
        }
        select{
            height:40px;
            background-color:$light-gray;
            margin:0 16px 16px 0;
            border:1px solid $border-gray;
            padding-left:8px;

        }
    }
      }
</style>
