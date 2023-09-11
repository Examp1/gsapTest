<template>
  <main>
    <section class="section">
      <h1>Basic ScrollTrigger in VueJS</h1>
      <h2 class="title">Scroll down to see the magic happen!!</h2>
    </section>
    <section class="section boxWrp" ref="main">
      <div class="innerContent" ref="innerContent">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
        <div class="box">box3</div>
      </div>
    </section>
    <section class="section flex-center orange column">
      <h1>The End!</h1>
    </section>
  </main>
</template>

<script>
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "HomeView",
  mounted() {
    let wrapper = this.$refs.main;
    const trg = this.$refs.innerContent
    let totalWidth = trg.scrollWidth - window.innerWidth;
    gsap.to(trg, {
      x: -totalWidth * 0.5,
      scrollTrigger: {
        trigger: wrapper,
        start: 'top center',
        end: 'bottom 50%',
        scrub: 2,
        pin: true
      }
    })
    // let boxes = wrapper.querySelectorAll(".box");
    // let totalWidth = boxes.length * window.innerWidth; // общая ширина всех блоков

    // gsap.to(wrapper, {
    //   x: `-=${totalWidth - window.innerWidth}`, // смещение на общую ширину минус ширина одного блока
    //   scrollTrigger: {
    //     trigger: wrapper,
    //     pin: true, // "закрепить" блок на месте
    //     start: "top top",
    //     end: `+=${totalWidth}`,
    //     scrub: true,
    //     invalidateOnRefresh: true,
    //   },
    // });
  },
};
</script>

<style lang="scss" scoped>
.section {
  position: relative;
  min-height: 100vh;
}
.boxWrp {
  overflow: hidden; // скрыть горизонтальную прокрутку
  width: 100%;
  height: 20vh;
}
.innerContent{
  width: 100%;
  height: 100%;
  display: flex;
  grid-gap: 40px;
}
.box {
  width: 50%;
  height: 400px;
  background-color: #91b946;
  flex-shrink: 0;
}
</style>
