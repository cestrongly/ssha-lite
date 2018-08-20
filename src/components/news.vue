<template lang="pug">
  //- news
  .news
    text.news-title {{title}}
    navigator.news-item__wrapper( 
      v-for="(item,index) in newsComputed", 
      :key="index",
      :url="item.url")
      .news-item.line
        .news-item-pic
          img.news-item-image(
            mode="widthFix",
            :src="item.pic")
        .news-item-words
          .news-item-title
            text.text {{item.title}}
          .news-item-content
            text.text {{item.content}}
    //-占位符
    slot
</template>

<script>
import _ from 'lodash'
export default {
  // 增加一个可从外部传入的属性initNum
  props: {
    newsTitle: {
      type: String,
      default: ''
    },
    news: {
      type: Array,
      default: []
    }
  },
  data () {
    return {
      title: this.newsTitle, // 使用传入的initNum值作为初始的点击数
      news: this.news
    }
  },
  // mpvue 不支持过滤器
  filters: {
    url (id) {
      return `/pages/news/news-details?id=${id}`
    }
  },
  computed: {
    // mpvue 不支持模板绑定函数
    getUrl () {
      return (id) => {
        return `/pages/news/news-details?id=${id}`
      }
    },
    newsComputed () {
      return _.map(this.news, (value) => {
        let obj = value
        obj.url = `/pages/news-detail/main?id=${value.id}`
        return obj
      })
    }
  },
  methods: {
    // mpvue 不支持模板绑定函数
    getUrl (id) {
      return `/pages/news/news-details?id=${id}`
    }
  }
}
</script>
<style lang="stylus">
.news 
  padding 26rpx 40rpx
.news-title
  color #aaa
.news-item
  margin 10rpx 0
  background-color #fff
.news-item-pic
  padding 20rpx 0 10rpx 20rpx
  width 160rpx
  float left
.news-item-image
  width 100%
.news-item-words
  width 450rpx
  height 130rpx
  float right
  overflow hidden
  padding 20rpx 10rpx
.news-item-title
  font-size 32rpx
  word-break break-all
  white-space nowrap
  overflow hidden
  text-overflow ellipsis
.news-item-content
  font-size 24rpx
  line-height 1.5
  color #a9a9a9
</style>

