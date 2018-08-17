<template>
  <div class="index">
    <!-- slider -->
    <div class="slider">
      <swiper class="swiper"
              :indicator-dots="indicatorDots"
              :autoplay="autoplay"
              :interval="interval"
              :duration="duration">
        <swiper-item 
          class="swiper-item" 
          v-for="(item,index) in swipers" 
          :key="index">
          <navigator :url="item.link" class="widget">
            <image mode="cover" :src="item.pic" class="slide-image"/>
          </navigator>
        </swiper-item>
      </swiper>  
    </div>
    <!-- end swiper -->
    <!-- news -->
    <news :newsTitle="news_title" :news="news">
      <div class="widgets__list widgets__list_show">
        <navigator class="widget__more" url="/pages/news/main">
          <text class="new-more">查看更多</text>
          <image class="widget__arrow" src="/static/assets/arrowright.png" mode="aspectFill" />
          <div class="widget__line widget__line_first"></div>
        </navigator>
      </div>
    </news>
    <!-- end news -->
  </div>
</template>
<script>
import './index.scss'
// 导入 News 组件
import News from '@/components/news'
export default {
  components: {
    // 声明在当前组件下使用 News 组件
    News
  },
  data () {
    return {
      title: '江苏盛世华安智能科技有限公司',
      swipers: [
        {'pic': 'http://www.jsssha.com/wp-content/uploads/2017/01/video.jpeg', 'link': '/pages/video/video'},
        {'pic': 'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg', 'link': ''}
      ],
      indicatorDots: false,
      autoplay: false,
      interval: 5000,
      duration: 1000,
      news_title: '新闻动态',
      news: [
        {
          'id': 0,
          'pic': 'http://www.jsssha.com/wp-content/uploads/2016/12/4-300x250.jpg',
          'title': '“创新发展 再创辉煌”盛世华安2016年度圣诞主题年会圆满落幕',
          'content': '2016年，对于盛世华安而言是一个机遇与挑战并存的一年，更是收获的一年。这一年在公司领导层的正确领导和支持下，全体员工齐心协力，顽强进取，各方面的工作都取得了一定的成绩。'
        },
        {
          'id': 1,
          'pic': 'http://www.jsssha.com/wp-content/uploads/2016/12/2-1-300x250.jpg',
          'title': 'CCIA第七届中国物联网产业与新型智慧城市年会圆满落幕，江苏盛世华安智能科技股份有限公司',
          'content': '2016年12月16日，由工业和信息化部指导，中国通信工业协会主办，中国通信工业协会物联网应用分会承办的“第七届中国物联网产业与新型智慧城市年会”在北京万寿宾馆隆重召开。'
        },
        {
          'id': 2,
          'pic': 'http://www.jsssha.com/wp-content/uploads/2016/11/572057806235746054-300x250.jpg',
          'title': '热烈祝贺东方金汇通成功申报软件企业',
          'content': '苏州东方金汇通智能科技有限公司是江苏盛世华安智能科技股份有限公司旗下一家专业从事智能化系统、计算机软硬件、电子产品研发的全资子公司'
        }
      ]
    }
  },
  /**
   * 小程序转发功能
   */
  onShareAppMessage () {
    // return custom share data when user share.
    console.log('onShareAppMessage')
    return {
      title: '盛世华安',
      desc: '小程序',
      path: '/pages/index/index'
    }
  }
}
</script>