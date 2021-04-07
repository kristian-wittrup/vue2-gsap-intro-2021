<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/projects">Projects</router-link>
    </div>
    <transition
      appear
      @beforeEnter="beforeEnter"
      @enter="enter"
      @leave="leave"
    >
      <router-view/>
    </transition>
  </div>
</template>


<script>
import gsap from 'gsap'
import TweenMax from 'gsap'

export default {
  methods: {
    beforeEnter: (el, done) => {
      gsap.from(el, {
        onComplete: done
      })
    },
   
    enter: (el, done) => {
      gsap.set(el, { 
        x: window.innerWidth * 1.5,
        scale: 0.8,
        transformOrigin: '50% 50%'
      })
      gsap.to(el, {
        x: 0,
        duration: 0.5,
        ease: 'power4.out',
        delay:0.5
      })
      gsap.to(el, {
        duration: 0.5,
        scale: 1,
        ease: 'power4.out',
        onComplete: done
      })
    },
    leave: (el, done) => {
      TweenMax.fromTo(el, {
        autoAlpha: 1 
      }, 
      {
        autoAlpha: 0,
        duration:0.5,
        ease: 'power4.out', 
        onComplete: done
      })
    }
  }
}
</script>





<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
