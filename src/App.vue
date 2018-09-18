<template>
  <div id="app">
    <div class="comm">
      <div class="hello">
        <ul>
          <li><router-link to=""><p class="iconfont icon-goumai"></p><b>收藏</b></router-link></li>
          <li><router-link to=""><p class="iconfont icon-dianpu1"></p><b>店铺</b></router-link></li>
          <li><router-link to=""><p class="iconfont icon-hanbao"></p><b>商品</b></router-link></li>
          <li><router-link to=""><p class="iconfont icon-huiyuanqia"></p><b>会员</b></router-link></li>
          <li><router-link to=""><p class="iconfont icon-tongji"></p><b>统计</b></router-link></li>
          <li><router-link to=""><p class="iconfont icon-gongnengjianyi"></p><b>设置</b></router-link></li>
        </ul>
      </div>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
  @import "assets/comm.css";
  @import "//at.alicdn.com/t/font_714714_ptol46rod2h.css";
  @import "assets/left.css";
  .comm{
    width: 10%;
    background: #0186E0;
    height: 100%;
    display: inline-block;
    vertical-align: top;
  }
  #app{width: 100%;height: 100%}
</style>
