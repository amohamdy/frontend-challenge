<template>
        <form id="search-form">
            <div id="search-form-input">
              <input type="search" v-model="searchText" placeholder="Search" name="search-query"
              class="base" @keydown.13.prevent="submitForm">
              <button class="search-btn" @click.prevent="submitForm">
                <svg viewBox="0 0 24 24" preserveAspectRatio="xMidYMid meet" focusable="false"
                class="style-scope yt-icon" style="pointer-events: none;
                display: block; width: 100%; height: 100%;"><g class="style-scope yt-icon">
                  <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3
                  9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5
                  4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14
                  7.01 14 9.5 11.99 14 9.5 14z" class="style-scope yt-icon"></path>
                </g></svg>
              </button>
            </div>
            <div id="responsive-search-form-input">
              <input type="search" v-model="searchText" placeholder="Search" name="search-query"
              class="base" v-show="isShow"
              @keydown.13.prevent="submitForm">
              <button class="search-btn" @click.prevent="isShow = !isShow">
                <svg viewBox="0 0 24 24" preserveAspectRatio="xMidYMid meet" focusable="false"
                class="style-scope yt-icon" style="pointer-events: none;
                display: block; width: 100%; height: 100%;"><g class="style-scope yt-icon">
                  <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3
                  9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5
                  4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14
                  7.01 14 9.5 11.99 14 9.5 14z" class="style-scope yt-icon"></path>
                </g></svg>
              </button>

            </div>
        </form>

</template>

<script>
// @ is an alias to /src
export default {
  name: 'SearchForm',
  data() {
    return {
      searchText: '',
      isShow: '',
    };
  },
  methods: {
    submitForm() {
      this.$emit('search-video', this.searchText);
    },
  },
};
</script>

<style scoped lang="scss">
  @import '../scss/mixins.scss';
  @import '../scss/variables.scss';
  #search-form{
    width:50%;
    border:1px solid $border-gray;
    border-radius:2px;
    margin:0 auto;
    @media screen and (max-width:991.98px){
      border:0;
      width:80%;
      margin:0;
      padding-right:1rem;
    }
    #search-form-input{
      height:40px;
      @include display-flex(row,flex-start,center);
      @media screen and (max-width:991.98px){
        display:none;
      }
      input{
        height:100%;
        border:0;
        padding:0;
        width:87%;
        padding:0 16px;
        &::placeholder{
          font-size:16px;
        }
        &:focus{
          box-shadow:none;
          outline:none;
        }
      }
      .search-btn{
        height:100%;
        border:0;
        width:13%;
        background-color:$light-gray;
        border-left:1px solid $border-gray;

        &:focus{
          box-shadow:none;
          outline:none;
          }
        svg{
          width:20px !important;
          height:20px !important;
          margin:auto;

        }
      }
    }
    #responsive-search-form-input{
      @include display-flex(row, flex-end,center);
      @media screen and (min-width:992px){
        display:none;
      }
      input{
        width:80%;
        height:40px;
        border:1px solid $border-gray;
        padding:8px;
        &.is-active{
          border:0;
          background-color: transparent;
        }
      }
      .search-btn{
        height:100%;
        border:0;
        width:13%;
        background-color: transparent;

        &:focus{
          box-shadow:none;
          outline:none;
          }
        svg{
          width:30px !important;
          height:30px !important;
          margin:auto;
          fill:#fff;

        }
      }
    }
  }

</style>
