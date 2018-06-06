<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="iconfont hd-back">&#xe624</div>
    </router-link>

  </div>
</template>

<script>
export default {
}
</script>
 <!-- reset.css里html的fontsize为50px，二倍尺寸图86px，则为.86rem -->
<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    position:relative
    overflow:hidden
    height:.86rem
    line-height:.86rem
    text-align:center
    color:#fff
    background:$bgColor
    .hd-back
      position:absolute
      top:0
      left:0
      width:.64rem
      text-align:center
      color:#fff
</style>