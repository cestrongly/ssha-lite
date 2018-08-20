<template lang="pug">
  .page
    .page__bd 新闻列表id: {{id}}
</template>
<script>
import './style.stylus'
// 导入 News 组件
import News from '@/components/news'
export default {
  components: {
    // 声明在当前组件下使用 News 组件
    News
  },
  data () {
    return {
      id: null
    }
  },
  mounted () {
    this.id = this.$root.$mp.query.id
  }
}
</script>
