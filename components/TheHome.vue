<template>
  <div class="container" id="fullpage">
    <section class="section-1 parallax" data-depth="0.2">
      <div class="caption">
        <div class="num">
          <span class="line">
            <span class="line_inner">/ 01</span>
          </span>
        </div>
        <div class="about">
          <div class="title">/ Digital Agency</div>
          <div class="desc">Elevating Brands through Digital Innovation.</div>
        </div>
      </div>
    </section>

    <section class="section-2 parallax" data-depth="1.2">
      <div class="s2-content">
        <div class="s2-title">/ Introduction</div>

        <div class="s2-text">Accelerating Global Brands — Years ahead.</div>
        <div class="s2-text">
          We are a world—class team of industry—leading professionals, who
          constantly push new technology to its limits.
        </div>
      </div>
    </section>

    <!-- <section class="section-3">
      <div class="s3-content">
        <div>/ The Agency</div>
        <div>We Provoke what's Possible.</div>
        <div>
          We're and award-winning strategic digital innovation agency. We fuse
          data with unrivaled creativity to achieve remarkable results for
          ambitious brands.
        </div>
      </div>
    </section> -->

    <div id="bg">
      <img src="~/assets/bg-1.jpg" />
    </div>
  </div>
</template>

<script setup>
const { gsap } = useGsap();

onMounted(() => {
  // const container = ref();
  // container.value = document.querySelector('.container');

  // const section1 = ref();
  // section1.value = document.querySelector('.section-1');

  // const section2 = ref();
  // section2.value = document.querySelector('section-2');

  // const parallax = ref(null);
  // parallax.value = document.querySelectorAll('.parallax');

  // const timeline = gsap.timeline({
  //   scrollTrigger: {
  //     trigger: container.value,
  //     start: 'top top',
  //     end: 'bottom top',
  //     scrub: true,
  //   },
  // });

  // gsap.utils.toArray(parallax.value).forEach((layer) => {
  //   const depth = layer.dataset.depth;
  //   const movement = -(layer.offsetHeight * depth);
  //   timeline.to(layer, { y: movement, ease: 'none' }, 0);
  // });

  // $(document).ready(function () {
  //   $('#fullpage').fullpage({
  //     anchors: ['firstPage', 'secondPage', 'thirdPage'],
  //     menu: '#menu',
  //     autoScrolling: false,
  //     // responsiveWidth: 750
  //   });
  // });

  // const fullpage = ref();
  // fullpage.value = new fullpage('#fullpage', {
  //   anchors: ['firstPage', 'secondPage', 'thirdPage'],
  //   menu: '#menu',
  //   autoScrolling: false,
  //   // responsiveWidth: 750
  // });

  const section2 = ref();
  section2.value = document.querySelector('.section-2');

  // ScrollMagic: init controller
  const timeline = gsap.timeline({
    scrollTrigger: {
      trigger: section2.value,
      start: 'top top',
      end: 'top top',
      scrub: true,
    },
  });

  timeline.set('#bg img', {
    maxWidth: '1200px',
    top: '30%',
    left: '80%',
    opacity: 0.25,
  });

  // Tween - Section 2
  // var scene = new ScrollMagic.Scene({
  //   triggerElement: '.section-2',
  //   triggerHook: 0,
  //   duration: '100%',
  // })
  //   .setTween('.section-2', {
  //     y: '50%',
  //     ease: Linear.easeNone,
  //   })
  //   .addTo(controller);
});
</script>

<style scoped>
.container {
  /* background: grey; */
  /* background: linear-gradient(#0f0f0c, #23231c); */
}
.section-1 {
  /* background: linear-gradient(#0f0f0c, #23231c); */
  height: 100vh;
  width: 100%;
}
.caption {
  font-size: 0.875rem;
  font-weight: 100;
  line-height: 1.5;
  color: #fff;
  position: absolute;
  left: 15vh;
}
.num {
  position: absolute;
  top: 60vh;
  width: 10vh;
}

.line {
}

.line_inner {
}

.about {
  position: absolute;
  left: 15vh;
  top: 60vh;
  width: 50vh;
}

.title {
}

.desc {
  position: relative;
  top: 5vh;
}

.section-2 {
  /* background: #0f0f0c; */
  color: #fff;
  padding: 100px;
  position: absolute;
  top: 100vh;
  width: 100%;
}

.s2-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.s2-title {
  font-size: 2rem;
  font-weight: 100;
}

.s2-text {
  font-size: 0.875rem;
  font-weight: 100;
  line-height: 1.5;
}

#bg {
  z-index: -1;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

#bg img {
  position: absolute;
  top: 60%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 100%;
  height: 600px;
  width: 600px;
  max-width: 900px;
}

.s3-content {
  /* display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 4px;
  gap: 4px;

  background: #eef1f7;
  border: 1px solid #000000;
  box-shadow: 3px 3px 0px #000000; */
}
</style>
