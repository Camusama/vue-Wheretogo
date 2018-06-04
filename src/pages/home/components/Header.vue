<template>
  <div class="header">
   <div class="header-left">
     <div class="iconfont back-icon">&#xe624</div>
   </div>
   <div class="header-input">
   <span class="iconfont">&#xe632</span>输入城市景点/游览主题</div>
   <div class="header-right ">城市<span class="iconfont arr-icon">&#xe64a</span></div>
  </div>
</template>

<script>
export default {
  data () {
    return {

    }
  }
}
</script>
 <!-- reset.css里html的fontsize为50px，二倍尺寸图86px，则为.86rem -->
<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    display:flex
    line-height:.86rem
    background:$bgColor
    color:#fff
    .header-left
      width:.64rem
      float:left
      .back-icon
        text-align:center
        font-size:.4rem
    .header-input
      flex:1
      height:.64rem
      line-height:.64rem
      margin:.12rem 0 0 .2rem
      padding-left:.2rem
      background:#fff
      border-radius:5px
      color:#ccc
    .header-right
      width:1.24rem
      text-align:center
      .arr-icon
        font-size:.24rem
</style>