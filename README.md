# vue-svg-homing-player
svgファイルを読み込み、それに関する情報を取得と操作を司るJSクラス

[DEMO](https://tktr90755.github.io/vue-svg-homing-player/)  

## Install
```
npm install git+https://github.com/tktr90755/vue-svg-homing-player.git
```

## Usage
![SAMPLE SVG](./public/test.svg)  
```js
let svgPlayer = new SvgPlayer();
svgPlayer.speed = 1;
svgPlayer.dispatcher.addEventListener(Event.INIT, ()=>{
    console.log("Event.INIT")
    svgPlayer.play()
    //使っているsvgはこれ
    document.getElementById('app').append(svgPlayer.svg)
});
svgPlayer.dispatcher.addEventListener(Event.START, ()=>{
    console.log("Event.START")
});
svgPlayer.dispatcher.addEventListener(Event.RENDER, ()=>{
    let x = svgPlayer.point.x;
    let y = svgPlayer.point.y;
    this.$el.style.left = x + "px";
    this.$el.style.top = y + "px";
    this.$el.style.transform = 'rotate(' + svgPlayer.rotation + 'deg)';
    console.log("Event.RENDER: percent:" + svgPlayer.percent + " x:" + x + " y:" + y + " rotation:" + svgPlayer.rotation )
});
svgPlayer.dispatcher.addEventListener(Event.COMPLETE, ()=>{
    console.log("Event.COMPLETE")
});
svgPlayer.load('test.svg', false)//第二引数をtrueにすると自動的にplay()する
```

---
## Vue CLI npm script

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```