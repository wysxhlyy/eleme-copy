<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img :src="seller.avatar" width="64" height="64">
      </div>
      <div class="content">
        <div class="title">
          <span class="brand"></span>
          <span class="name">{{seller.name}}</span>
        </div>
        <div class="description">
          {{seller.description}}/{{seller.deliveryTime}}分钟送达
        </div>
        <div v-if="seller.supports" class="support">
          <span class="icon" :class="classMap[seller.supports[0].type]"></span>
          <span class="text">{{seller.supports[0].description}}</span>
          <!--加v-if因为ajax请求是异步的，刚开始seller.supports是undefined，无法取到0-->
        </div>
      </div>
      <div v-if="seller.supports" class="support-count">
        <span class="count">{{seller.supports.length}}个</span>
        <!--<i class="icon-keyboard_arrow_right"></i>-->
      </div>
    </div>



    <div class="bulletin-wrapper">
      <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
      <!--<i class="icon-keyboard_arrow_right"></i>-->

    </div>

    <div class="background">
      <img :src="seller.avatar" width="100%" height="100%">
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default{
    props: {
      seller: {
        type: Object
      }
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
    }
  };
</script>

<style lang="scss" rel="stylesheet/scss">

  @import "../../common/scss/support.scss";
  /*@import "../../common/stylus/icon.styl";*/

  .header{
    position: relative;
    background: rgba(7,17,27,0.5);
    color: #fff;

    .content-wrapper{
      position: relative;
      padding: 24px 12px 18px 24px;
      font-size: 0;

      .avatar{
        display: inline-block;
        vertical-align: top;

        img{
          border-radius: 4px;
        }
      }

      .content{
        display: inline-block;
        margin-left: 16px;

        .title{
          margin: 2px 0 8px 0;

          .brand{
            display: inline-block;
            vertical-align: top;
            width: 30px;
            height: 18px;
            background-size: 30px 18px;
            background-repeat: no-repeat;
            @include bg-image('brand')
          }

          .name{
            margin-left: 6px;
            font-size: 16px;
            line-height: 18px;
            font-weight: bold;
          }
        }

        .description{
          margin-bottom: 10px;
          line-height: 12px;
          font-size: 12px;
        }

        .support{
          .icon{
            display: inline-block;
            vertical-align: top;
            width: 12px;
            height: 12px;
            margin-right: 4px;
            background-size: 12px 12px;


            &.decrease{
              @include bg-image('decrease_1');
             };

            &.discount{
             @include bg-image('discount_1');
             };

            &.guarantee{
             @include bg-image('guarantee_1');
             };

            &.invoice{
             @include bg-image('invoice_1');
             };

            &.special{
             @include bg-image('special_1');
             };

          }

          .text{
            line-height: 12px;
            font-size: 10px;
          }
      }
    }
    .support-count{
      position: absolute;
      right: 12px;
      bottom: 14px;
      padding: 0 8px;
      height: 24px;
      line-height: 24px;
      border-radius: 14px;
      background: rgba(0,0,0,0.2);
      text-align: center;

      .count{
        vertical-align: top;
        font-size: 10px;
      }
      .icon-keyboard_arrow_right{
        margin-left: 2px;
        line-height: 24px;
        font-size: 10px;
      }
    }

  }

  .bulletin-wrapper{
    position: relative;
    height: 28px;
    line-height: 28px;
    padding: 0 22px 0 12px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    background:rgba(7,17,27,0.2);


    .bulletin-title{
      display: inline-block;
      vertical-align: top;
      margin-top: 8px;
      margin-right: 4px;
      width: 22px;
      height: 12px;
      background-size: 22px 12px;
      background-repeat: no-repeat;
      @include bg-image('bulletin');
    }

    .bulletin-text{
      vertical-align: top;
      font-size: 10px;
    }
    .icon-keyboard_arrow_right{
      position: absolute;
      font-size: 10px;
      right: 12px;
      top:8px;
    }
  }

  .background{
    position: absolute;
    top:0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    filter: blur(10px);
  }


  }







</style>
