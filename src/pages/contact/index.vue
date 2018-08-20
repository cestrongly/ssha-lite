<template lang="pug">
  .page
    .page__bd
      .section.section__gap
        map(
          style="width: 100%; height: 300px"
          :latitude="latitude"
          :longitude="longitude"
          :scale="scale"
          :markers="markers")
        .contact
          text 
            | 股票：838280\n
            | 电话：0512-58161723\n
            | 传真：0512-58161711\n
            | 地址：江苏省苏州市张家港市滨河路2号\n华东国际大厦5F
</template>
<script>
import './style.stylus'
// import currentPage from '@/utils/current-page'
export default {
  data () {
    return {
      title: '联系我们',
      latitude: 31.838403,
      longitude: 120.528958,
      scale: 16,
      markers: [
        {
          latitude: 31.838403,
          longitude: 120.528958,
          name: '华东国际大厦5F'
        }
      ]
    }
  },
  mounted () {
    this.getInfo()
    // console.log(currentPage.getCurrentPageUrl(getCurrentPage()))
  },
  methods: {
    getInfo () {
      console.log(this)
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