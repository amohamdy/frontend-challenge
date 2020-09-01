<template>
<label class="container">{{item}}
  <input type="radio"  name="radio"   v-model="selected">
  <span class="checkmark"></span>
</label>
</template>

<script>
export default {
  name: 'CustomRadio',
  props: ['item'],
  data() {
    return {
      selected: '',
    };
  },
};
</script>

<style scoped lang="scss">
    .container {
        display: block;
        position: relative;
        margin-bottom: 12px;
        cursor: pointer;
        font-size: 22px;
        user-select: none;
        input{
            position: absolute;
            opacity: 0;
            cursor: pointer;
            height: 0;
            width: 0;
            &:checked{
                ~ .checkmark{
                      background-color: transparent;
                      &:after{
                            display: block;

                      }
                }
            }

        }
        .checkmark {
            position: absolute;
            top: 0;
            left: 0;
            height: 25px;
            width: 25px;
            background-color: transparent;
            &:after{
                content: 'X';
                position: absolute;
                display: none;
                  left: 9px;
                top: 5px;
                width: 5px;
                height: 10px;
                border: solid white;
                border-width: 0 3px 3px 0;

            }
            }

    }

</style>
