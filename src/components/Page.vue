<template>
  <div>
    <h1>Ramen Timer</h1>
    <img class="ramen-img" src="../assets/ramen.jpg" alt="ramen">
    <Timer />
    <How />
  </div>
</template>

<script>
import Timer from'./atoms/Timer.vue'
import How from'./atoms/How.vue'

export default {
  name: 'Page',
  components: {
    Timer,
    How
  }
}
</script>

<style scoped>
.buttons{
  display: flex;
  justify-content: center;
}
.ramen-img{
  width: 60vw;
  border-radius: 50%;
  border: #efefef 1px solid; 
  margin: 0 0 30px 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
