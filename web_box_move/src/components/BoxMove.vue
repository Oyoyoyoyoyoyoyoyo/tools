<template>
  <div>
    <div
      class="boxMoveBody"
      v-on:mousedown="mouseDownFun($event)"
      v-on:mousemove="mouseMoveFun($event)"
      v-on:mouseup="mouseUpFun($event)"
    >
      <div>body</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "选中移动",
  data() {
    return {
      screen: {
        x: 500,
        y: 500,
      },
      moveParams: {
        x: 0,
        y: 0,
        l: 0,
        t: 0,
      },
      isDown: false,
    };
  },
  watch: {},
  mounted() {},
  methods: {
    mouseDownFun(e) {
      // 获取浏览器尺寸
      this.screen.x = document.body.clientWidth;
      this.screen.y = document.body.clientHeight;
      this.moveParams.x = e.clientX;
      this.moveParams.y = e.clientY;
      //获取左部和顶部的偏移量
      this.moveParams.l = e.target.offsetLeft;
      this.moveParams.t = e.target.offsetTop;
      //开关打开
      this.isDown = true;
      //设置样式
      e.target.style.cursor = "move";
    },
    mouseMoveFun(e) {
      if (this.isDown == false) {
        return;
      }
      //获取x和y
      var nx = e.clientX;
      var ny = e.clientY;
      //计算移动后的左偏移量和顶部的偏移量
      var nl = nx - (this.moveParams.x - this.moveParams.l);
      var nt = ny - (this.moveParams.y - this.moveParams.t);

      nl < 0 && (nl = 0);
      nl > this.screen.x && (nl = this.screen.x);
      nt < 0 && (nt = 0);
      nt > this.screen.y && (nt = this.screen.y);
      e.target.style.left = nl + "px";
      e.target.style.top = nt + "px";
    },
    mouseUpFun(e) {
      //开关关闭
      this.isDown = false;
      e.target.style.cursor = "default";
    },
  },
};
</script>

<style>
.boxMoveBody {
  width: 100px;
  height: 100px;
  background-color: blue;
  position: absolute;
  z-index: 10000;
}
</style>
