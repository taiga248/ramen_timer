<template>
  <div>
    <div class="buttons">
      <button @click="startTimer(text[0])">{{text[0]}}</button>
      <button @click="startTimer(text[1])">{{text[1]}}</button>
    </div>
    <div class="time">
      {{min + ":" + sec}}
    </div> 
  </div>
</template>

<script>
export default {
  name: 'Timer',
  data: () => {
    return {
      text: [3, 5],
      min: 0,
      sec: 0,
      count: false, // trueの時はタイマーが動いている
      bell: {
        src: require('../../assets/bell.mp3')
      },
      ring: new Audio(),
    }
  },
  methods:{
    startTimer: function(time){
      this.toggleCounter()
      let timer = time * 60

      let timerObj = setInterval(() =>{
        timer -= 1
        this.counter(timer)

        if(timer === 0){
          this.toggleCounter()
          this.reset(timerObj)
          this.chime()
        }else if (this.count === false){ 
          this.toggleCounter()
          this.reset(timerObj)
          timerObj // 他のボタンが押された時 再始動
        }
      }, 1000)
    },

    counter: function (timer){
      this.sec = timer % 60
      this.min = Math.floor( timer / 60 )
    },

    reset: function(timerObj){
      clearInterval(timerObj)
    },

    toggleCounter: function(){
      this.count = !this.count
    },

    chime: function(){
      this.ring.src = this.bell.src
      this.ring.play()
    }
  }
}
</script>

<style scoped>
.buttons{
  display: flex;
  justify-content: center;
  margin: 0 0 20px 0;
}
.time{
  font-size: 2em;
}
button {
  width: 100px;
  height: 50px;
  font-size: 1.75em;
  border-radius: 10px;
  background: #fff;
  margin: 0 10px;
}
</style>
