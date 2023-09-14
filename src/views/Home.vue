<template>
  <main>
    <section class="section">
      <div class="ticker">
        <div class="text-wrap" ref="textWrap">
          <div class="text">Бегущая строка текста...</div>
          <div class="text">Бегущая строка текста...</div>
        </div>
      </div>
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
    const wrapper = this.$refs.main;
    const trg = this.$refs.innerContent;
    let totalWidth = trg.scrollWidth - window.innerWidth;
    gsap.to(trg, {
      x: -totalWidth * 0.5,
      scrollTrigger: {
        trigger: wrapper,
        start: "top center",
        end: totalWidth,
        scrub: 2,
        pin: true,
      },
    });

    const textWrap = this.$refs.textWrap;
    const textWidth = textWrap.firstElementChild.offsetWidth;

    gsap.set(textWrap, { x: 0 });
    gsap.to(textWrap, {
      x: -textWidth,
      repeat: -1,
      ease: "linear",
      duration: 5,
    });

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
.innerContent {
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
.ticker {
  overflow: hidden;
  white-space: nowrap;
  width: 100vw;
  position: relative;
}

.text-wrap {
  display: flex;
  width: 100%;
  font-size: 220px;
}

.text {
  white-space: nowrap;
  display: inline-block;
  // width: 100vw;
}
</style>
