<template>
    <div class="click-couter">
        <div class="counter-num">次数:{{num}}</div>
        <button class="counter-btn" @click="handleClick">点我呀</button>
        <button class="couter-reset-btn" @click="handleResetClick">清零</button> 
    </div>
</template>

<script>
export default {
  data () {
    return {
      num: 0
    }
  },

  methods: {
    handleClick () {
      this.num += 1
    },
    handleResetClick () {
      this.num = 0
    }
  }
}
</script>

<style>
.click-couter {
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid red;
  background-color: #fff;
  padding: 10px;
}
.counter-num,
.counter-btn,
.couter-reset-btn {
  flex: 1;
  margin: 3px;
}
</style>

