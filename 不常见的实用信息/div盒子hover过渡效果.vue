<template>
  <div class="hello">
    <div class="outer-wrapper">
      <div class="box">
        <img src="../assets/logo.png">
      </div>
      <div class="hover-wrapper">
        <img src="../assets/hover.png">
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
  .hello{
    padding: 20px;
    text-align: center;
  }
.outer-wrapper{
  width: 100px;
  height: 100px;
  border: 1px solid #ddd;
  transition: all 0.4s;
  position: relative;
  img{
    width: 100%;
  }
  .box{
    position: absolute;
    left: 0;
    top: 0;
    transition: all 0.5s;
  }
  .hover-wrapper {
    position: absolute;
    left: 0;
    top: 0;
    opacity: 0;
    transform: scale(1.333, 1.333);
    transition: all 0.4s;
  }
  &:hover{
    .box{
      opacity: 0;
      transform: scale(0.2);
    }
    .hover-wrapper{
      opacity: 1;
      transform: scale(1, 1);
    }
  }
}
</style>
