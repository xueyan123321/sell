<template>
    <span class="text border-1px">
      <span class="icon" :class="classMap[item.type]"></span>{{item.name}}
    </span>
</template>

<script type="text/ecmascript-6">

</script>

<style lang="scss"
       rel="stylesheet/scss">
  .icon{
    display:inline-block;
    width: 12px;
    height: 12px;
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
</style>
