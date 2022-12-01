<template>
  <div class="bubble-wrapper">
    <div ref="bubble" class="bubble">
      <img class="bubble-image" src="~/assets/selfie.png" alt="icon" />
    </div>
    <div ref="bubblePulse" class="bubble-pulse"></div>
  </div>
</template>

<script setup>
onMounted(() => {
  const { gsap } = useGsap();

  const bubble = ref(null);
  bubble.value = document.querySelector('.bubble');

  const bubblePulse = ref(null);
  bubblePulse.value = document.querySelector('.bubble-pulse');

  const timeline = gsap.timeline({
    onComplete: () => timeline.restart(),
  });

  timeline.to(bubble.value, {
    duration: 0.4,
    scale: 0.8,
    rotation: 16,
    ease: 'back.out(1.7)',
  });
  timeline.to(
    bubblePulse.value,
    {
      duration: 0.4,
      scale: 0.9,
      opacity: 1,
    },
    '-=0.6'
  );

  timeline.to(bubble.value, {
    duration: 1.2,
    scale: 1,
    rotation: '-=16',
    ease: 'elastic.out(2.5, 0.5)',
  });
  timeline.to(
    bubblePulse.value,
    {
      duration: 1.1,
      scale: 3,
      opacity: 0,
      ease: 'expo.out',
    },
    '-=1.2'
  );
});
</script>

<style>
.bubble-wrapper {
  position: absolute;
}
.bubble {
  position: relative;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid white;
  background: #272727;
  border-radius: 50%;
  height: 100px;
  width: 100px;
}
.bubble-pulse {
  position: absolute;
  z-index: 1;
  height: 120px;
  width: 120px;
  top: 50%;
  left: 50%;
  margin-top: -60px;
  margin-left: -60px;
  background: #272727;
  border-radius: 50%;
  opacity: 0;
  transform: scale(0);
}
.bubble-image {
  height: 50%;
  background: #272727;
}
</style>
