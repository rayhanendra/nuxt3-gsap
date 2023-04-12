<template>
  <div class="ball"></div>
</template>

<script setup>
const { gsap } = useGsap();

onMounted(() => {
  const ball = ref(null);
  ball.value = document.querySelector('.ball');

  gsap.set(ball.value, {
    xPercent: -50,
    yPercent: -50,
  });

  const pos = { x: window.innerWidth / 2, y: window.innerHeight / 2 };
  const mouse = { x: pos.x, y: pos.y };
  const speed = 0.2;

  const xSet = gsap.quickSetter(ball.value, 'x', 'px');
  const ySet = gsap.quickSetter(ball.value, 'y', 'px');

  window.addEventListener('mousemove', (e) => {
    mouse.x = e.x;
    mouse.y = e.y;
  });

  // adjust the ball's position
  gsap.ticker.add(() => {
    const dt = 1.0 - Math.pow(1.0 - speed, gsap.ticker.deltaRatio());
    pos.x += (mouse.x - pos.x) * dt;
    pos.y += (mouse.y - pos.y) * dt;
    xSet(pos.x);
    ySet(pos.y);
  });
});
</script>
<style scoped>
/* body {
  background-color: black;
  font-family: 'Signika Negative', sans-serif;
  color: white;
  text-align: center;
} */

.ball {
  width: 50px;
  height: 50px;
  position: fixed;
  top: 0;
  left: 0;
  border: 3px solid dodgerblue;
  border-radius: 50%;
  pointer-events: none;
}
</style>
