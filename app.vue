<template>
  <div>
    <!-- <NuxtWelcome />
     -->
    <div>Hello!</div>
    <div ref="box" class="box"></div>
    <div class="center">
      <TheBubble />
    </div>
  </div>
</template>

<script>
export default {
  setup() {
    const { gsap } = useGsap();

    onMounted(() => {
      const box = ref(null);
      box.value = document.querySelector('.box');

      const timeline = gsap.timeline({
        onComplete: () => timeline.restart(),
      });
      timeline.to(box.value, {
        duration: 1,
        x: 500,
        rotation: 360,
        ease: 'back.inOut', // https://greensock.com/docs/v3/Eases
      });
      timeline.to(
        box.value,
        {
          duration: 0.5,
          backgroundColor: 'green',
        },
        '-=0.5' // https://greensock.com/docs/v3/TimeLine#add()
      );
    });
  },
};
</script>

<style scoped>
.box {
  height: 60px;
  width: 60px;
  background: red;
}

.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
