<template>
  <div>
    <!-- <div class='hidden&#45;disp' id="app"> -->
    <!--   <img alt="Vue logo" src="./assets/logo.png"> -->
    <!--   <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- </div> -->
    <div :class='["err-area", errClass]'>{{notification}}</div>
    <BasicBindings 
      :title='title'/>
    <CssAnimation 
      @notification='noteHandling'
      :initialColor='"#22d"'
    />
    <CssAnimation 
      @notification='alert'
    />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import BasicBindings from './components/basic_bindings.vue'
import CssAnimation from './components/css_animation.vue'

export default {
  name: 'app',
  data () {
    return {
      notification: "testes",
      title: "タイトル",
      errClass: 'err-hidden'
    }
  },
  components: {
    HelloWorld,
    BasicBindings,
    CssAnimation
  },
  methods: {
    noteHandling: function (errObj) {
      this.notification = errObj.message
      this.activateError()
    },
    alert: function (err){
      alert(err.message)
    },
    activateError: function () {
      this.errClass = 'err-appear'
      setTimeout(() => this.errClass = 'err-hidden', 3000)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.hidden-disp{
  display: none;
}
.err-area{
  position: absolute;
  width: 90rem;
  height: 10rem;
  background: #f77;
  color: #fff;
  z-index: 10;
  transition: 0.5s;
}
.err-hidden{
  top: -100rem;
}
.err-appear{
  top: 0rem;
}
</style>
