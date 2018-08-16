<template>
  <div class="container">
    <button open-type="getUserInfo" v-if="isShow" @getuserinfo="bindGetUserInfo" @click="getUserInfo1">获取权限</button>

    <div class="panel form-panel">
      <div v-if="isShowUserInfo" class="userinfo">
        <image class="userinfo-avatar" :src="userInfo.avatarUrl" background-size="cover"></image>
        <div class="userinfo-nickname">{{userInfo.nickName}}</div>
      </div>
      <div class="form-items">
        <div class="form-item-group">
          <div class="form-item-block">
            <label class="label" for="password">设置口令</label>
            <input class="input-text" type="text" id="password">
          </div>
          <div class="text">小伙伴们说对口令就能领随机金额的红包</div>
        </div>
        <div class="form-item-block">
          <label class="label" for="amount">总&nbsp;金&nbsp;额</label>
          <input class="input-text" type="digit" id="amount" placeholder="填写红包总金额(元)" placeholder-style="color:#ccc" placeholder-class="placeholder">
        </div>
        <div class="form-item-block">
          <label class="label" for="amount">红包个数</label>
          <input class="input-text" type="number" ra id="amount" placeholder="填写个数" placeholder-style="color:#ccc" placeholder-class="placeholder">
        </div>
        <div class="form-item-group">
          <div class="option">
            <div class="text center">需要支付￥0.00服务费</div>
            <button class="btn">生成语音红包</button>
          </div>
        </div>
      </div>
    </div>

    <div class="ad-area">
      <div class="text">这里是广告板</div>
    </div>

    <div class="btn-area">
      <navigator class="navigator" url="main" hover-class="navigator-hover">我的记录</navigator>
      <div class="text split">|</div>
      <navigator class="navigator" url="main" open-type="redirect" hover-class="other-navigator-hover">联系客服</navigator>
    </div>
  </div>

</template>

<script>
// 导入 click-counter 组件
import ClickCounter from '@/components/click-counter'
import globalStore from '@/stores/global-store'

export default {
  components: {
    // 声明在当前组件下使用 counter-click 组件
    ClickCounter
  },
  data () {
    return {
      msg: 'Hello',
      height: 'height: 0px',
      inputValue: 0,
      userInfo: {},
      isShow: false,
      isShowUserInfo: false
    }
  },
  created () {

  },
  mounted () {
    // 一进来看看用户是否授权过
    this.getSetting()
  },
  methods: {
    getSetting () {
      let that = this
      wx.getSetting({
        success (res) {
          if (res.authSetting['scope.userInfo']) {
            wx.getUserInfo({
              success (res) {
                console.log(res.userInfo)
                that.userInfo = res.userInfo
                that.isShow = false
                // 用户已经授权过
                console.log('用户已经授权过')
              }
            })
          } else {
            console.log('用户还未授权过')
            that.isShow = true
          }
          that.isShowUserInfo = !that.isShow
        }
      })
    },
    getUserInfo1 () {
      console.log('click事件首先触发')
      // 判断小程序的API，回调，参数，组件等是否在当前版本可用。  为false 提醒用户升级微信版本
      // console.log(wx.canIUse('button.open-type.getUserInfo'))
      if (wx.canIUse('button.open-type.getUserInfo')) {
        // 用户版本可用
      } else {
        console.log('请升级微信版本')
      }
    },
    bindGetUserInfo (e) {
      // console.log(e.mp.detail.rawData)
      if (e.mp.detail.rawData) {
        // 用户按了允许授权按钮
        console.log('用户按了允许授权按钮')
      } else {
        // 用户按了拒绝按钮
        console.log('用户按了拒绝按钮')
      }
    }
  },
  computed: {
    count () {
      return globalStore.state.count
    }
  }
}
</script>

<style scoped>
.container {
  width: 100%;
  min-height: 100%;
  background: #f1f1f1;
  font-size: 32rpx;
}
.text {
  font-size: 24rpx;
  color: #999;
}
.center {
  text-align: center;
}
.form-panel {
  margin-top: 107rpx;
  margin-left: 34rpx;
  margin-right: 34rpx;
  background-color: #fff;
}
.form-items {
  margin: 60rpx;
  margin-bottom: 0;
}
.form-items .input-text {
  border-bottom: 1rpx solid #d9d9d9;
}
.placeholder{
    color: #18acff;
}
.form-item-block {
  margin: 20rpx 0;
  display: flex;
  align-items: center;
}
.form-item-block .label{
  width: 150rpx;
}
.form-item-block .input-text {
  padding-top:4rpx;
  flex: 1;
}
.userinfo {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  transform: translateY(-50rpx);
}
.userinfo-avatar {
  border-radius: 50%;
  width: 134rpx;
  height: 134rpx;
  border: 10rpx solid #fff;
}
.option {
  padding: 50rpx;
}
.btn {
  margin: 10rpx 0;
  background-color: #c96148;
  border-radius: 44rpx;
  height: 88rpx;
  color: #fff;
}
.ad-area {
  margin: 20rpx 34rpx;
  background-color: #fff;
  padding: 20rpx;
}
.ad-area .text {
  background-color: #282828;
  color: #fff;
  font-size: 96rpx;
  text-align: center;
}
.btn-area {
  display: flex;
  align-content: center;
  justify-content: center;
  align-items: center;
}
.text.split {
  margin: 0 20rpx;
  color: #ccc;
}
.navigator {
  color: #5c6b91;
  font-size: 28rpx;
}
</style>