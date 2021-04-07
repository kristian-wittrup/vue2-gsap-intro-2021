<template>
  <div class="about">
    <transition
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
    >
    
      <h1>This is an about page</h1>

    </transition>


      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Eius doloremque exercitationem illum dolore suscipit optio minus distinctio, odit natus sit laborum facere. Vero iste amet, possimus voluptatibus sunt blanditiis eligendi.
        Ipsum obcaecati officiis aliquam minima incidunt officia. Saepe, nesciunt. Maxime provident quia voluptatum! Ratione ipsam quia nihil dolorum. Accusamus numquam officiis iusto officia blanditiis minima aliquam quis nesciunt vel repellendus.
        Voluptate eligendi sit culpa cupiditate aperiam quasi magni inventore commodi eius recusandae harum, temporibus maxime atque enim aliquam. Veniam laboriosam repellendus adipisci. Dignissimos nostrum odit ullam qui quisquam iusto adipisci.
        Dicta numquam porro nulla doloremque amet est voluptatem, minima laudantium sint repellendus totam ab odio perferendis dolorem vitae praesentium quod cum voluptatibus earum aspernatur nobis soluta. Vitae quos praesentium alias?
      </p>

  </div>
</template>

<script>
import gsap from "gsap"

export default {
  methods: {
    beforeEnter: (el) => {
      console.log("beforeEnter")
      /*el.style.transform = 'translateY(-60px)'
      el.style.opacity = 0*/
      gsap.from(el, {
        y: -60,
        opacity:0
      })
    },
   
    enter: (el, done) => {
      console.log("Enter")
      gsap.to(el, { 
        duration: 3,
        y: 0,
        opacity: 1,
        ease: "elastic.out(1, 0.3)",
        onComplete: done
      })
    },
     
    afterEnter: (el) => {
      console.log("AfterEnter")
      gsap.to(el, {
        duration: 2,
        y: -60,
        opacity: 0
      })
    }
  }
}
</script>