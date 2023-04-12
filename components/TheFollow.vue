<template>
  <div id="Wrap">
    <img
      class="FollowBox"
      src="https://source.unsplash.com/Pd8tLVGx2O4/200x250"
      alt=""
    />
  </div>
</template>

<script setup>
const { gsap } = useGsap();

onMounted(() => {
  const FollowBox = ref(null);
  FollowBox.value = document.querySelector('#Wrap .FollowBox');
  gsap.set(FollowBox.value, {
    xPercent: -50,
    yPercent: -50,
    scale: 0,
  });

  window.addEventListener('mousemove', (e) => {
    gsap.to(FollowBox.value, {
      duration: 0.5,
      overwrite: 'auto',
      x: e.clientX,
      y: e.clientY,
      stagger: 0.15,
      ease: 'none',
    });

    const timeline = gsap.timeline({
      defaults: {
        duration: 0.5,
        ease: 'none',
      },
    });

    timeline.to(FollowBox.value, {
      scale: 1,
      overwrite: 'auto',
      stagger: {
        amount: 0.15,
        from: 'start',
        ease: 'none',
      },
    });

    timeline.to(
      FollowBox.value,
      {
        scale: 0,
        overwrite: 'auto',
        stagger: {
          amount: 0.15,
          from: 'end',
          ease: 'none',
        },
      },
      '<+=2.5'
    );
  });
});
</script>

<style scoped>
:root {
  font-family: Helvetica;
}

::-webkit-scrollbar {
  display: none;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#Wrap {
  position: relative;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: none;
  overflow: hidden;
}

#Wrap .FollowBox {
  position: absolute;
  top: 0;
  left: 0;
  width: 200px;
  height: 250px;
}

#Wrap .FollowBox {
  z-index: 4;
}
</style>
