<template>
  <svg>
    <use 
      :xlink:href="dvdHref"
      :width="width"
      :x="x" 
      :y="y"
      ref="dvd"
    ></use>
  </svg>
</template>

<script>
export default {
  data:()=>({
    dvdHref: require('~/assets/dvd.svg')+'#svg-dvd',
    width:100,
    x:100,
    y:100
  }),
  mounted(){
      this.v = { x: 3, y: 3 }
      this.height = this.$refs.dvd.getBoundingClientRect().height
      window.addEventListener('keydown',e=>{
        if (e.keyCode == 37)      this.v.x-=1
        else if (e.keyCode == 39) this.v.x+=1
        else if (e.keyCode == 38) this.v.y-=1
        else if (e.keyCode == 40) this.v.y+=1
      })

      this.render()
  },
  methods:{
    render(){
      requestAnimationFrame(this.render.bind(this))
      if (this.x < 0 || window.innerWidth < this.x+this.width ) this.v.x *= -1
      if (this.y < 0 || window.innerHeight < this.y+this.height) this.v.y *= -1
      this.x += this.v.x
      this.y += this.v.y
    }
  }
}
</script>

<style>
div,svg{
    width: 100%;
    height: 100%;
    display: block;
    margin:0;
    padding: 0;
}
</style>
