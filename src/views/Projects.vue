<template>
  <div class="projects">

    <transition-group
      appear
      @before-enter="beforeEnter"
      @enter="enter"
    >
    
      <div id="project-container" v-for="(project, index) in projects" :key="project.name" :data-index="index">
        <h3>{{project.name}}</h3> 
        <p>{{project.description}}</p> 
      </div>

    </transition-group>
  </div>
</template>

<script>
import gsap from 'gsap'

  export default {
    methods: {
      beforeEnter: (el) => {
        gsap.from(el, {
          y: 100,
          opacity: 0,
          delay: el.dataset.index * 1 // remember to change time to show
        })
      },
      enter: (el, done) => {
        gsap.to(el, {
          duration: 1,
          y: 0,
          opacity: 1,
          ease: 'bounce.out',
          onComplete: done,
          delay: el.dataset.index * 1
        })
      }
    },


    data() {
      return {
        projects: [
          {
            name: "Project one",
            description: "Description one"
          },
          {
            name: "Project two",
            description: "Description two"
          },
          {
            name: "Project three",
            description: "Description three"
          }
        ]
      }
    },
  }
</script>

<style lang="scss">
#project-container {
  background-color: lightgray;
  width: 300px;
  height: 100px;
  margin: 10px auto;
  padding: 10px 0;
}
</style>