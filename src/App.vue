<script>
export default {
  created () {
    console.log('miniapp created!!!')
  }
}
</script>

<style>
page {
  display: flex;
  background-color: #F8F8F8;
  font-family: -apple-system-font,Helvetica Neue,Helvetica,sans-serif;
  min-height: 100%;
  line-height: 1.6;
}
view {
  word-break: break-all;
  overflow: auto;
}
.page {
  background-color: #FBF9FE; 
  font-family: -apple-system-font,Helvetica Neue,Helvetica,sans-serif;
  flex: 1;
  min-height: 100%;
  font-size: 32rpx;
}
.page__bd {
  padding-bottom: 40px;
}
</style>
