<template>
  <div style="height: 100%;position:absolute;width:100%;">
    <nav style="height: 40px;position:absolute;width:100%">我是导航</nav>
    <section
      style="position:absolute;left:0;right:0;height:auto;top:40px;"
    >
      没错我就是内容区域，可多可多了
      dev1
      dev2
    </section>
    <footer
      id="footer"
      style="position: absolute;bottom:0;width:100%;"
    >

      <input
        class="ipt"
        type="text"
        placeholder="在这里输入"
        style="outline:none;width:80%;height: 40px;"
      />
      <p style="">
        这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字这里有很多很多的文字多的文字这里有很多很多的文字这里有很多很多的文字多的文字这里有很多很多的文字这里有很多很多的文字
      </p>
    </footer>
  </div>
</template>
<script>
import $ from 'jquery'

export default {
  name: 'HelloWorld',
  components: {},
  data() {
    return {
      footerHeight: '',
      winHeight: ''
    }
  },
  created() {},
  mounted() {
    const ff = document.getElementById('footer')
    this.$nextTick(() => {
      this.winHeight = $(window).height()
      this.footerHeight = ff.scrollHeight
      console.log(this.footerHeight)
    })
    const h = document.body.scrollHeight
    $(window).resize(() => {
      if (document.body.scrollHeight < h) {
        this.handleFocus()// 得焦
      } else {
        this.onBlur()// 失焦
      }
    })

    // $(window).resize(function() {
    //   console.log('resize1')
    //     var thisHeight = $(this).height();
    //     var k = thisHeight - winHeight;
    //     $("#footer").css({ 'bottom': k + 'px' });
    // });
  },
  methods: {
    onBlur () {
      console.log('失焦')
      const ele = $('#footer').css({
        position: 'fixed',
        marginTop: 0
      })
    },

    handleFocus(e) {
      console.log('得焦')
      const that = this
      $('#footer').css({
        position: 'static',
        marginTop: that.winHeight - this.footerHeight + 'px'
      })
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
* {
  margin: 0;
  padding: 0;
}

html,
body,
#app {
  background: #fff;
  font-size: 20px;
  width: 100%;
  height: 100%;
}
.a {
  height: 100%;
  display: flex;
  flex-direction: column;
}
.main {
  height: 100%;
  border: 1px solid blue;
}
.inner {
  height: 100%;
  /* height: auto; */
}
.footer {
  background: yellow;
}

/* 可以设置不同的进入和离开动画 */
/* 设置持续时间和动画函数 */
.slide-fade-enter-active {
  transition: all 2s ease;
}
.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active for below version 2.1.8 */ {
  opacity: 0;
}
.slide-fade-leave-to {
  transform: translateX(10px);
}
td {
  width: 300px;
}
</style>
