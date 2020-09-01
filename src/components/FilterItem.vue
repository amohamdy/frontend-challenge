<template>
    <div>
        <div class="filter-item" @click="isSelected = !isSelected">{{item}}
        <img src="../assets/close.png" v-if="isSelected">
        </div>
    </div>
</template>

<script>
export default {
  name: 'FilterItem',
  props: ['item'],
  data() {
    return {
      isSelected: false,
    };
  },
  // methods: {
  //   toggleSelected() {
  //     isSelected = !isSelected;
  //   },
  // },

};
</script>

<style scoped lang="scss">
    img{
    // display:none;
    width:15px;
    height:15px;
    float:right;
}
</style>
