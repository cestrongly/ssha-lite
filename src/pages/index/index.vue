<template>
  <div class="container" @click="clickHandle">
    <div class="message">{{msg}}</div>
    <!-- 使用 click-counter 组件 -->
    <click-counter :init-num="10" @clicknum="handeClickNum">
      <input type="checkbox"> 禁用
    </click-counter>
    <div>计数结果: {{count}}</div>
    <a href="/pages/test1/main" class="navlink">进入计数器页面</a>
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
      inputValue: 0
    }
  },
  methods: {
    clickHandle () {
      this.msg = 'Clicked!!!!!!'
    },
    handeClickNum (data) {
      console.log('>>>>>>>>>', data.num)
      this.height = `height: ${data.num}px`
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
.message {
  color: red;
  padding: 10px;
  text-align: center;
}
.box {
  /* border: 1px solid red; */
}
.navlink {
  text-decoration: underline;
}
</style>