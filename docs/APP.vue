<template lang='pug'>
  #app(v-cloak)
    #header
      .mask
      img.logo(src="~icons/256x256.png", alt="PicGo")
      h1.title PicGo
      h2.desc 图片上传+管理新体验
      button.download(@click="goLink('https://github.com/Molunerfinn/picgo/releases')") 免费下载Mac版
      button.download(@click="goLink('https://github.com/Molunerfinn/picgo/releases')") 免费下载Windows版
      button.download(@click="goLink('https://github.com/Molunerfinn/picgo')") 在github上查看
      h3.desc
        | 基于#[a(href="https://github.com/SimulatedGREG/electron-vue" target="_blank") electron-vue]开发
    #container.container-fluid
      .row.ex-width
        img.gallery.col-xs-10.col-xs-offset-1.col-md-offset-2.col-md-8(src="https://ws1.sinaimg.cn/large/8700af19gy1fmayjwttnbj218g0p0q4e")
      .row.ex-width.display-list
        .display-list__item(v-for="(item, index) in itemList" :key="index" :class="{ 'o-item': index % 2 !== 0 }")
          .col-xs-10.col-xs-offset-1.col-md-7.col-md-offset-0
            img(:src="item.url")
          .col-xs-10.col-xs-offset-1.col-md-5.col-md-offset-0.display-list__content
            .display-list__title {{ item.title }} 
            .display-list__desc {{ item.desc }}
      .row.ex-width.info
        .col-xs-10.col-xs-offset-1
          | &copy;2017 #[a(href="https://github.com/Molunerfinn" target="_blank") Molunerfinn]
</template>
<script>
export default {
  name: '',
  data () {
    return {
      itemList: [
        {
          url: 'https://ws1.sinaimg.cn/large/8700af19ly1fma907llb5j20m30ed46a',
          title: '精致设计',
          desc: 'macOS系统下，支持拖拽至menubar图标实现上传。menubar app 窗口显示最新上传的5张图片以及剪贴板里的图片。点击图片自动将上传的链接复制到剪贴板。（Windows平台不支持）'
        },
        {
          url: 'https://ws1.sinaimg.cn/large/8700af19ly1fmd56zm2nej218g0p0teb',
          title: '便捷管理',
          desc: '查看你的上传记录，重复使用更方便。支持点击图片大图查看。支持删除图片（仅本地记录），让界面更加干净。'
        },
        {
          url: 'https://ws1.sinaimg.cn/large/8700af19ly1fmd5ck9m0wj20lr0cxmzs',
          title: '可选图床',
          desc: '目前支持微博图床、七牛图床、腾讯云COS、又拍云。未来将支持更多。方便不同图床的上传需求。'
        },
        {
          url: 'https://ws1.sinaimg.cn/large/8700af19gy1fmayjwttnbj218g0p0q4e',
          title: '多样链接',
          desc: '支持4种剪贴板链接格式，让你的文本编辑游刃有余。'
        }
      ]
    }
  },
  methods: {
    goLink (link) {
      window.open(link, '_blank')
    }
  }
}
</script>
<style lang='stylus'>
[v-cloak]
  display none
*
  box-sizing border-box
body,
html,
h1
  margin 0
  padding 0
  font-family "Source Sans Pro","Helvetica Neue","PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif  
#app
  position relative
.mask
  position absolute
  width 100%
  height 100vh
  top 0
  left 0
  background rgba(0,0,0, 0.7)
  z-index -1
#header
  height 100vh
  width 100%
  background-image url("https://ws1.sinaimg.cn/large/8700af19ly1fm9ru6fqvjj22p81stdta")
  background-attachment fixed
  background-size cover
  background-position center
  text-align center
  padding 15vh
  position relative
  z-index 2
  .logo
    width 120px
  .title
    color #4BA2E2
    font-size 36px
    font-weight 300
    margin 10px auto
  .desc
    font-weight 400
    margin 20px auto 10px
    color #ddd
    a
      text-decoration none
      color #4BA2E2
  .download
    display inline-block
    line-height 1
    white-space nowrap
    cursor pointer
    background transparent
    border 1px solid #d8dce5
    color #ddd
    -webkit-appearance none
    text-align center
    box-sizing border-box
    outline none
    margin 20px 12px
    transition .1s
    font-weight 500
    user-select none
    padding 12px 20px
    font-size 14px
    border-radius 20px
    padding 12px 23px
    transition .2s all ease-in-out
    &:hover
      background #ddd
      color rgba(0,0,0, 0.7)
#container
  position relative
  text-align center
  margin-top -10vh
  z-index 3
  .gallery
    margin-bottom 60px
    cursor pointer
    transition all .2s ease-in-out
    &:hover
      transform scale(1.05)
  .display-list
    &__item
      padding 48px
      text-align left
      background #2E2E2E
      overflow hidden
      &.o-item
        background #fff
        .display-list__desc
          color #2E2E2E
      img
        width 100%
        cursor pointer
        transition all .2s ease-in-out
        &:hover
          transform scale(1.05)
    &__content
      padding-top 120px
    &__title
      color #4BA2E2
      font-size 50px
    &__desc
      color #fff
      margin-top 20px
  .info
    padding 48px 0
    background #2E2E2E
    color #fff
    a
      text-decoration none
      color #fff
@media (max-width: 768px)
  #header
    padding 10vh
  #container
    .display-list
      &__item
        padding 24px 12px
      &__content
        padding-top 30px
      &__title
        font-size 25px
      &__desc
        margin-top 12px
</style>