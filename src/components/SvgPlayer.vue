<template>
  <div>→</div>
</template>

<script>
import SvgPlayer from '@/assets/js/libs/tk90755/media/SvgPlayer.js'
import Event from '@/assets/js/libs/tk90755/events/Event.js'
export default {
  props: {
    name: String
  },
  created(){

  },
  mounted(){
    let svgPlayer = new SvgPlayer();
    svgPlayer.speed = 1;
    svgPlayer.addEventListener(Event.INIT, ()=>{
      console.log("Event.INIT")
      svgPlayer.play()
      //使っているsvgはこれ
      document.getElementById('app').append(svgPlayer.svg)
      svgPlayer.svg.style.position = 'fixed';
      svgPlayer.svg.style.left = '0px';
      svgPlayer.svg.style.top = '0px';
      svgPlayer.svg.style.zIndex = '-1';
      svgPlayer.svg.style.width = '1366px';
      svgPlayer.svg.style.height = '768px';
    });
    svgPlayer.addEventListener(Event.START, ()=>{
      console.log("Event.START")
    });
    svgPlayer.addEventListener(Event.RENDER, ()=>{
      let x = svgPlayer.point.x - 10;
      let y = svgPlayer.point.y - 15;
      this.$el.style.position = 'fixed';
      this.$el.style.fontSize = '30px';
      this.$el.style.left = x + "px";
      this.$el.style.top = y + "px";
      this.$el.style.zIndex = '1';
      this.$el.style.transform = 'rotate(' + svgPlayer.rotation + 'deg)';
      console.log("Event.RENDER: percent:" + svgPlayer.percent + " x:" + x + " y:" + y + " rotation:" + svgPlayer.rotation )
    });
    svgPlayer.addEventListener(Event.COMPLETE, ()=>{
      console.log("Event.COMPLETE")
    });
    svgPlayer.load(this.name + '.svg', false)//第二引数をtrueにすると自動的にplay()する
  }
}
</script>