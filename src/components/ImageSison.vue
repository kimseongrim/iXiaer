<template>
  <div
    id="image-sison"
    :style="urlStyle"
  >
    <img
      :src="url"
      height="0"
      width="0"
      @load="loaded"
    >
  </div>
</template>

<script>
import { LoadingBar } from 'iView'

export default {
  name: 'ImageSison',
  data () {
    return {
      // require()访问时会经过url-loader, 会对文件及路径做处理
      url: require('../assets/images/sison.jpg')
    }
  },
  computed: {
    urlStyle: function () {
      return 'background:url(' + this.url + ') center'
    }
  },
  mounted: function () {
    // 启动进度条
    LoadingBar.start()
  },
  methods: {
    loaded: function () {
      // 结束进度条
      LoadingBar.finish()
    }
  }
}
</script>

<!-- scoped是作用域标签，里面所有的声明只在此组件生效 -->
<style scoped>
#image-sison {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
}
</style>
