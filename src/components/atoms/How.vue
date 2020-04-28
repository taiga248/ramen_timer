<template>
  <div>
    <p v-if="show" @click="toggle">How to use</p>
    <div v-else class="explan">
      This application is very simple.<br>
      It just tells you when the ramen is ready.<br>
      It has no other function.<br>
      For now, try pushing the button.
      <p @click="toggle">close</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Timer',
  data: () => {
    return {
      show: true
    }
  },
  methods:{
    toggle: function(){
      this.show = !this.show
    }
  }
}
</script>

<style scoped>
div{
  margin: 10px 0 0 0;
}
p{ 
  color: #42b983; 
  font-size: 1em;
}
</style>
