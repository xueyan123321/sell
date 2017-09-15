<template>
    <span class="text border-1px">
      <span v-show="iconType>0" class="icon" :class="classMap[iconType]"></span>{{text}}
    </span>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      iconType: Number,
      text: String
    },
    data() {
      return {
        classMap: ['decrease', 'discount', 'special', 'invoice', 'guarantee']
      };
    }
  };
</script>

<style lang="scss"
       rel="stylesheet/scss" scoped>
  @import "../../common/sass/mixin.scss";
  .icon{
    display:inline-block;
    width: 18px;
    height: 18px;
    vertical-align: top;
    margin-right: 2px;
    background-size: 16px 16px;
    background-repeat: no-repeat;
    &.decrease{
      @include bg-image('decrease_3')
    }
    &.discount{
      @include bg-image('discount_3')
    }
    &.guarantee{
      @include bg-image('guarantee_3')
    }
    &.invoice{
      @include bg-image('invoice_3')
    }
    &.special{
      @include bg-image('special_3')
    }
  }
  .text{
    display: table-cell;
    width:56px;
    vertical-align: middle;
    @include border-1px(rgba(7,17,27,0.1));
    font-size: 12px;
  }
</style>
