<template>
  <div>
    <!-- <img src="~/assets/dream.svg" class="dream" /> -->
    <svg
      width="94"
      height="678"
      viewBox="0 0 94 678"
      fill="blue"
      xmlns="http://www.w3.org/2000/svg"
      class="dream"
    >
      <path
        d="M47 0L69.5167 613.5H24.4833L47 0Z"
        fill="white"
        class="dreamTail"
      />
      <path
        d="M94 631C94 656.957 72.9574 678 47 678C21.0426 678 0 656.957 0 631C0 605.043 21.0426 584 47 584C72.9574 584 94 605.043 94 631Z"
        fill="white"
        class="dreamHead"
      />
    </svg>
  </div>
</template>

<script setup>
const { gsap } = useGsap();

onMounted(() => {
  const dream = ref();
  dream.value = document.querySelector('.dream');

  const dreamTail = ref();
  dreamTail.value = document.querySelector('.dreamTail');

  //   const dreamTailPath = ref();
  //   dreamTailPath.value = dreamTail.value.getAttribute('d');

  const dreamHead = ref();
  dreamHead.value = document.querySelector('.dreamHead');

  const tl = gsap.timeline({
    onComplete: () => tl.restart(),
  });
  tl.to(dreamTail.value, {
    duration: 0.6,
    opacity: randomNumber(0.6, 0.2),
    ease: 'RoughEase.ease.config({ template: Power0.easeOut, strength:1, points: 20, taper: "both", randomize: true, clamp: false})',
  });
  tl.to(dreamHead.value, {
    duration: 1,

    opacity: randomNumber(1, 0.6),
    ease: 'RoughEase.ease.config({ template: Power0.easeOut, strength:1, points: 20, taper: "both", randomize: true, clamp: false})',
  });
});

const randomNumber = (max = 1, min = 0) => {
  return Math.random() * (max - min + min);
};
</script>

<style scoped>
.dream {
  width: 100%;
  height: 80%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;

  /* transform: scale(1.3); */
  filter: blur(10.5px) drop-shadow(0px 18px 47px #ffffff);
}
</style>
