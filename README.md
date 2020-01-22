# Vue-Drag-And-Drop
Simple way to drag and drop a shape 

![ezgif com-video-to-gif](https://user-images.githubusercontent.com/23725255/72885438-34050b80-3d08-11ea-84b2-d0f470b2e938.gif)

### Created your shape (circle)

```html
<div
  class="circle-drag"
  :style="circlePostition"
  @mousedown="circlePress"
  @mousemove="circleMove"
  @mouseup="circleRelease"
></div>

```
### Put your data
Default position of shape 


```js
data() {
  return {
    posX: 50,
    posY: 50,
    isPress: false
  };
},
``` 

### Add methods for press, move and release your shape

```js
methods: {
  circlePress() {
    // shape is pressed ?
    this.isPress = true;
  },
  circleMove(e) {
    if (this.isPress) {
      // delta between mouse pos and shape pos
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
```
### Bind your style as computed

```js
computed: {
  circlePostition() {
    return {
      // move shape (top/left)
      top: this.posY - 25 + "px", // (25) 50% of circle shape
      left: this.posX - 25 + "px"
    };
  }
}
``` 
