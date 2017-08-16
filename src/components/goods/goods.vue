<template>
  <div class="goods">
    <div class="menu-wrapper">
      <ul>
        <li v-for="item in goods" class="menu-item">

        </li>
      </ul>
    </div>
    <div class="foods-wrapper"></div>
  </div>
</template>

<script type="text/ecmascript-6">
  const ERR_OK = 0;
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    data() {
      return {
        goods: [],
        classMap: []
      };
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
      this.axios.get('/api/goods').then((response) => {
        if (response.data.errno === ERR_OK) {
          this.goods = response.data.data;
        }
      });
    }
  };
</script>

<style lang="scss"
       rel="stylesheet/scss">
  @import "../../common/sass/mixin.scss";

  .goods{
    display:flex;
    position:absolute;
    top:174px;
    bottom:46px;
    width:100%;
    overflow: hidden;
    .menu-wrapper{
      flex: 0 0 80px;
      width: 80px;
      background: #f3f5f7;
      .menu-item{
        display: table;
        height:54px;
        width:56px;
        padding: 0 12px;
        line-height:14px;
      }
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
      .text{
        display: table-cell;
        width:56px;
        vertical-align: middle;
        @include border-1px(rgba(7,17,27,0.1));
        font-size: 12px;
      }
    }
    .foods-wrapper
    {
      flex: 1;
    }
  }

</style>
