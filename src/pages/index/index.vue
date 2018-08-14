<template>
  <div class="container" @click="clickHandle">
    <div class="message">{{msg}}</div>
    <!-- 使用 click-counter 组件 -->
    <click-counter :init-num="10" @clicknum="handeClickNum"/>
    <!-- 组件的复用 -->
    <click-counter :init-num="20" @clicknum="handeClickNum"/>
    <click-counter :init-num="30" @clicknum="handeClickNum"/>
    <click-counter :init-num="40" @clicknum="handeClickNum"/>
    <div class="box" :style="height">高度会变化</div>
  </div>
  
</template>

<script>
// 导入 click-counter 组件
import ClickCounter from '@/components/click-counter'

export default {
  components: {
    // 声明在当前组件下使用 counter-click 组件
    ClickCounter
  },
  data () {
    return {
      msg: 'Hello',
      height: 'height: 0px'
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
  border: 1px solid red;
}
</style>