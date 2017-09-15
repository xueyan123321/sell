<template>
  <div class="goods">
    <div class="menu-wrapper">
      <ul>
        <li v-for="item in goods" class="menu-item">
          <icon :iconType="item.type" :text="item.name"></icon>
        </li>
      </ul>
    </div>
    <div class="foods-wrapper">
      <ul>
        <li v-for="item in goods" class="food-list">
          <h1 class="title">{{item.name}}</h1>
          <ul>
            <li v-for="food in item.foods" class="food-item border-1px">
              <div class="icon">
                <img  :src="food.icon">
              </div>
              <div class="content">
                <h2 class="name">{{food.name}}</h2>
                <p class="desc">{{food.description}}</p>
                <div class="extra">
                  <span class="count">月售{{food.sellCount}}份</span>
                  <span>好评率{{food.rating}}%</span>
                </div>
                <div class="price">
                  <span class="now">￥{{food.price}}</span>
                  <span class="old" v-show="food.oldPrice">￥
                    {{food.oldPrice}}</span>
                </div>
              </div>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import icon from '../icon/icon';
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
      this.axios.get('/api/goods').then((response) => {
        if (response.data.errno === ERR_OK) {
          this.goods = response.data.data;
        }
      });
    },
    components: {
      icon
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
    }
    .foods-wrapper
    {
      flex: 1;
      .title{
        padding-left: 14px;
        height: 26px;
        line-height: 26px;
        border-left: 2px solid #d9dde1;
        font-size:12px;
        color:rgb(147,153,159);
        background: #f3f5f7;
      }
      .food-item{
        display:flex;
        margin: 18px;
        padding-bottom: 18px;
        @include border-1px(rgba(7,17,27,0.1));
        &:last-child{
          @include border-none();
          margin-bottom: 0;
          .icon{
            flex: 0 0 57px;
            margin-right: 10px;
          }
        }
        .content{
          flex: 1;
          .name{
            margin: 2px 0 8px 0;
            height: 14px;
            line-height: 14px;
            font-size: 14px;
            color:rgb(7,17,27)
          }
          .desc,.extra{
            margin-bottom: 8px;
            line-height: 10px;
            font-size:10px;
            color:rgb(147,153,159)
          }
          .desc{
            margin-bottom: 8px;

          }
          .extra{
            line-height: 10px;
            &.count{
              margin-right: 12px;
            }
          }
          .price{
            font-weight: 700;
            line-height: 24px;
            .now{
              margin-right: 8px;
              font-size:14px;
              color:rgb(240,20,20)
            }
            .old{
              text-decoration: line-through;
              font-size:10px;
              color:rgb(147,153,159)
            }
          }
        }
      }
    }
  }

</style>
