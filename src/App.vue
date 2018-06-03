<template>
  <div id="app">
    <div class='title'>better-scroll 使用例子</div>
    1、<router-link to='/demo1' class='demo' tag='div'><a>最简单的滚动例子</a></router-link>
    <div class='demo'>2、下拉刷新例子</div>
    <div class='demo'>3、上拉加载例子</div>
    <div class='demo'>demo</div>
    <div class='demo'>demo</div>
    <router-view class='wai'>
      <div class='context'>
        <h1>startX</h1>
        类型：Number,
        默认值：0
        作用：横轴方向初始化位置。
        <h1>startY</h1>
        类型：Number,<br>
        默认值：0<br>
        作用：纵轴方向初始化位置，见 Demo 。
        <h1>scrollX</h1>
        类型：Boolean<br>
        默认值: false<br>
        作用：当设置为 true 的时候，可以开启横向滚动。<br>
        备注：当设置 eventPassthrough 为 'horizontal' 的时候，该配置无效。
        <h1>scrollY</h1>
        类型：Boolean<br>
        默认值：true<br>
        作用：当设置为 true 的时候，可以开启纵向滚动。<br>
        备注：当设置 eventPassthrough 为 'vertical' 的时候，该配置无效。
        <h1>freeScroll</h1>
        类型：Boolean<br>
        默认值：false<br>
        作用：有些场景我们需要支持横向和纵向同时滚动，而不仅限制在某个方向，这个时候我们只要设置 freeScroll 为 true 即可。<br>
        备注：当设置 eventPassthrough 不为空的时候，该配置无效。<br>
        <h1>directionLockThreshold</h1>
        类型：Number<br>
        默认值：5（不建议修改）<br>
        作用：当我们需要锁定只滚动一个方向的时候，我们在初始滚动的时候根据横轴和纵轴滚动的绝对值做差，当差值大于 directionLockThreshold 的时候来决定滚动锁定的方向。<br>
        备注：当设置 eventPassthrough 的时候，directionLockThreshold 设置无效，始终为 0。
        <h1>eventPassthrough</h1>
        类型： String<br>
        默认值：''<br>
        可选值：'vertical'、'horizontal'<br>
        作用：有时候我们使用 better-scroll 在某个方向模拟滚动的时候，希望在另一个方向保留原生的滚动（比如轮播图，我们希望横向模拟横向滚动，而纵向的滚动还是保留原生滚动，我们可以设置 eventPassthrough 为 vertical；相应的，如果我们希望保留横向的原生滚动，可以设置eventPassthrough为 horizontal）。<br>
        备注：eventPassthrough 的设置会导致其它一些选项配置无效，需要小心使用它。
        <h1>click</h1>
        类型：Boolean<br>
        默认值：false<br>
        作用：better-scroll 默认会阻止浏览器的原生 click 事件。当设置为 true，better-scroll 会派发一个 click 事件，我们会给派发的 event 参数加一个私有属性 _constructed，值为 true。
        <h1>tap</h1>
        类型：Boolean | String<br><br>
        默认值：false<br><br>
        作用：因为 better-scroll 会阻止原生的 click 事件，我们可以设置 tap 为 true，它会在区域被点击的时候派发一个 tap 事件，你可以像监听原生事件那样去监听它，如 element.addEventListener('tap', doSomething, false);。如果 tap 设置为字符串, 那么这个字符串就作为自定义事件名称。如 tap: 'myCustomTapEvent'。
        <h1>bounce</h1>
        类型：Boolean | Object<br>
        默认值：true<br>
        作用：当滚动超过边缘的时候会有一小段回弹动画。设置为 true 则开启动画。<br>
        bounce: {<br>
          top: true,<br>
          bottom: true,<br>
          left: true,<br>
          right: true<br>
        }<br>
        自 1.10.0 版本以后，bounce 可以支持关闭某些边的回弹效果，可以设置对应边的 key 为 false 即可。
        <h1>bounceTime</h1>
        类型：Number<br>
        默认值：800（单位ms，不建议修改）<br>
        作用：设置回弹动画的动画时长。
        <h1>momentum</h1>
        类型：Boolean<br>
        默认值：true<br>
        作用：当快速在屏幕上滑动一段距离的时候，会根据滑动的距离和时间计算出动量，并生成滚动动画。设置为 true 则开启动画。
        <h1>momentumLimitTime</h1>
        类型：Number<br>
        默认值：300（单位ms，不建议修改）<br>
        作用：只有在屏幕上快速滑动的时间小于 momentumLimitTime，才能开启 momentum 动画。
        <h1>momentumLimitDistance</h1>
        类型：Number<br>
        默认值：15（单位px，不建议修改）<br>
        作用：只有在屏幕上快速滑动的距离大于 momentumLimitDistance，才能开启 momentum 动画。
        <h1>swipeTime</h1>
        类型：Number<br>
        默认值：2500（单位ms，不建议修改）<br>
        作用：设置 momentum 动画的动画时长。
        <h1>swipeBounceTime</h1>
        类型：Number<br>
        默认值：500（单位ms，不建议修改）<br>
        作用：设置当运行 momentum 动画时，超过边缘后的回弹整个动画时间。
        <h1>deceleration</h1>
        类型：Number<br>
        默认值：0.001（不建议修改）<br>
        作用：表示 momentum 动画的减速度。
        <h1>flickLimitTime</h1>
        类型：Number<br>
        默认值：200（单位ms，不建议修改）<br>
        作用：有的时候我们要捕获用户的轻拂动作（短时间滑动一个较短的距离）。只有用户在屏幕上滑动的时间小于 flickLimitTime ，才算一次轻拂。
        <h1>flickLimitDistance</h1>
        类型：Number<br><br>
        默认值：100（单位px，不建议修改）<br><br>
        作用：只有用户在屏幕上滑动的距离小于 flickLimitDistance ，才算一次轻拂。
        <h1>resizePolling</h1>
        类型：Number<br><br>
        默认值：60（单位ms，不建议修改)
        作用：当窗口的尺寸改变的时候，需要对 better-scroll 做重新计算，为了优化性能，我们对重新计算做了延时。60ms 是一个比较合理的值。
        <h1>probeType</h1>
        类型：Number<br><br>
        默认值：0<br><br>
        可选值：1、2、3<br><br>
        作用：有时候我们需要知道滚动的位置。当 probeType 为 1 的时候，会非实时（屏幕滑动超过一定时间后）派发scroll 事件；当 probeType 为 2 的时候，会在屏幕滑动的过程中实时的派发 scroll 事件；当 probeType 为 3 的时候，不仅在屏幕滑动的过程中，而且在 momentum 滚动动画运行过程中实时派发 scroll 事件。如果没有设置该值，其默认值为 0，即不派发 scroll 事件。
        <h1>preventDefault</h1>
        类型：Boolean<br>
        默认值：true<br>
        作用：当事件派发后是否阻止浏览器默认行为。这个值应该设为 true，除非你真的知道你在做什么，通常你可能用到的是 preventDefaultException。
        <h1>preventDefaultException</h1>
        类型：Object<br>
        默认值：{ tagName: /^(INPUT|TEXTAREA|BUTTON|SELECT)$/}<br>
        作用：better-scroll 的实现会阻止原生的滚动，这样也同时阻止了一些原生组件的默认行为。这个时候我们不能对这些元素做 preventDefault，所以我们可以配置 preventDefaultException。默认值 {tagName: /^(INPUT|TEXTAREA|BUTTON|SELECT)$/}表示标签名为 input、textarea、button、select 这些元素的默认行为都不会被阻止。<br>
        备注：这是一个非常有用的配置，它的 key 是 DOM 元素的属性值，value 可以是一个正则表达式。比如我们想配一个 class 名称为 test 的元素，那么配置规则为 {className:/(^|\s)test(\s|$)/}。
        <h1>HWCompositing</h1>
        类型：Boolean<br>
        默认值：true（不建议修改）<br>
        作用：是否开启硬件加速，开启它会在 scroller 上添加 translateZ(0) 来开启硬件加速从而提升动画性能，有很好的滚动效果。<br>
        备注：只有支持硬件加速的浏览器开启才有效果。
        <h1>useTransition</h1>
        类型：Boolean<br>
        默认值：true（不建议修改）<br>
        作用：是否使用 CSS3 transition 动画。如果设置为 false，则使用 requestAnimationFrame 做动画。<br>
        备注：只有支持 CSS3 的浏览器开启才有效果。
        <h1>useTransform</h1>
        类型：Boolean<br>
        默认值：true（不建议修改）<br>
        作用：是否使用 CSS3 transform 做位移。如果设置为 false, 则设置元素的 top/left (这种情况需要 scroller 是绝对定位的)。<br>
        备注：只有支持 CSS3 的浏览器开启才有效果。
        <h1>bindToWrapper</h1>
        类型：Boolean<br>
        默认值：false<br>
        作用：move 事件通常会绑定到 document 上而不是滚动的容器上，当移动的过程中光标或手指离开滚动的容器滚动仍然会继续，这通常是期望的。当然你也可以把 move 事件绑定到滚动的容器上，bindToWrapper 设置为 true 即可，这样一旦移动的过程中光标或手指离开滚动的容器，滚动会立刻停止。
        <h1>disableMouse</h1>
        类型：Boolean<br>
        默认值：根据当前浏览器环境计算而来（不建议修改）<br>
        作用：当在移动端环境（支持 touch 事件），disableMouse 会计算为 true，这样就不会监听鼠标相关的事件，而在 PC 环境，disableMouse 会计算为 false，就会监听鼠标相关事件，不建议修改该属性，除非你知道你在做什么。
        <h1>disableTouch</h1>
        类型：Boolean<br>
        默认值：根据当前浏览器环境计算而来（不建议修改）<br>
        作用：当在移动端环境（支持 touch 事件），disableTouch 会计算为 false，这样会监听 touch 相关的事件，而在 PC 环境，disableTouch 会计算为 true，就不会监听 touch 相关事件。不建议修改该属性，除非你知道你在做什么。
        <h1>observeDOM(v1.5.3+)</h1>
        类型：Boolean<br>
        默认值：true<br>
        作用：会检测 scroller 内部 DOM 变化，自动调用 refresh 方法重新计算来保证滚动的正确性。它会额外增加一些性能开销，如果你能明确地知道 scroller 内部 DOM 的变化时机并手动调用 refresh 重新计算，你可以把该选项设置为 false。
        <h1>autoBlur(v1.7.0+)</h1>
        类型：Boolean<br>
        默认值：true<br>
        作用：在滚动之前会让当前激活的元素（input、textarea）自动失去焦点。
        <h1>stopPropagation(v1.9.0+)</h1>
        类型：Boolean<br>
        默认值：false<br>
        作用：是否阻止事件冒泡。
      </div>
    </router-view>
  </div>
</template>

<script>
export default {
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  position: absolute;
  bottom: 0px;
  top: 0px;
  margin-top:50px;
  width:100%;
  text-align: center;
}
.title {
  font-size: 30px;
  font-weight: 150px;
  margin-bottom:50px;
}
.demo{
  margin:25px 6px;
  display: inline-block;
  width: 160px;
  text-align: left;
}
ul,li{
    list-style: none;
    margin: 0px;
    padding: 10px;
}
.wai{
  width: 450px;
  height: 500px;
  border: 1px #424242 solid;
  margin: 0px auto;
  overflow: hidden;
  text-align: left;
  padding: 8px;
}
</style>
