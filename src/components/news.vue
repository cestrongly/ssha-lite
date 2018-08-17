<template>
  <!-- news -->
  <div class="news">
    <text class="news-title">{{title}}</text>
    <navigator 
      v-for="(item,index) in news" 
      :key="index" class="news-item__wrapper" 
      :url="'/pages/news/news-details?id=' + item.id">
      <div class="news-item line">
        <div class="news-item-pic">
          <image mode="widthFix" 
          :src="item.pic" 
          class="news-item-image" />
        </div>
        <div class="news-item-words">
          <div class="news-item-title">
            <text class="text">{{item.title}}</text>
          </div>
          <div class="news-item-content">
            <text class="text">{{item.content}}</text>
          </div>
        </div>
      </div>
    </navigator>
    <!-- 占位符 -->
    <slot></slot>
  </div>
  <!-- end news -->
</template>

<script>
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

  methods: {
  }
}
</script>

<style lang="scss" scoped>
.news {
  padding: 26rpx 40rpx;
}
.news-title {
  color: #aaa;
}
.news-item {
  margin: 10rpx 0;
  background-color: #fff;
}
.news-item-pic {
  padding: 20rpx 0 10rpx 20rpx;
  width: 160rpx;
  float: left;
}
.news-item-image {
  width: 100%;
}
.news-item-words {
  width: 450rpx;
  height: 130rpx;
  float: right;
  overflow: hidden;
  padding: 20rpx 10rpx;
}
.news-item-title {
  font-size: 32rpx;
  word-break: break-all;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.news-item-content {
  font-size: 24rpx;
  line-height: 1.5;
  color: #a9a9a9;
}
</style>

