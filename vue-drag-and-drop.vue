<template>
  <div
    class="circle-drag"
    :style="circlePostition"
    @mousedown="circlePress"
    @mousemove="circleMove"
    @mouseup="circleRelease"
  ></div>
</template>

<script>
export default {
  data() {
    return {
      posX: 50,
      posY: 50,
      isPress: false
    };
  },
  methods: {
    circlePress() {
      // shape is pressed ?
      this.isPress = true;
    },
    circleMove(e) {
      if (this.isPress) {
        // delta between mouse pos and shape pose
        var deltaX = e.clientX - this.posX;
        var deltaY = e.clientY - this.posY;
        this.posX += deltaX;
        this.posY += deltaY;
      }
    },
    circleRelease() {
      // shape release
      this.isPress = false;
    }
  },
  computed: {
    circlePostition() {
      return {
        // move shape (top/left)
        top: this.posY - 25 + "px", // 50% of circle shape
        left: this.posX - 25 + "px"
      };
    }
  }
};
</script>

<style lang="scss">
.circle-drag {
  position: absolute;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: blue;
  border: solid 5px black;
  border-color: black;
}
</style>
