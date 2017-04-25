<template>
  <div>
    <div class="header">
      <v-header></v-header>
    </div>
    <div class="tab border-1px">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <div class="content">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
  import header from 'components/header/header.vue';

  export default{
    components: {
      'v-header': header
    }
  };
</script>

<style lang="scss" rel="stylesheet/scss">
  @import "common/scss/support.scss";
  .tab {
    display: flex;
    width: 100%;
    height: 40px;
    line-height: 40px;
    @include border-1px(rgba(7,17,27,0.1));
    /*border-bottom: 1px solid rgba(7,17,27,0.1); !* 这样写在不同的屏幕上显示不同*!*/

    .tab-item {
      flex: 1;
      text-align: center;
    }

    a {
      display: block;
      font-size: 14px;
      color: rgb(77,85,93);
    }

    .active {
      color: rgb(240,20,20);
    }
  /* 点击时变红*/

  }


</style>
