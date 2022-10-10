<script setup>
  import gsap from "gsap";

  function onEnter(el, done) {
    gsap.from(el, {
      y: "-100vh",
      ease: "expo.inOut",
      duration: 3,
      onComplete: done,
    });
  }

  function onLeave(el, done) {
    gsap.to(el, {
      y: "100vh",
      ease: "expo.inOut",
      duration: 3,
      onComplete: done,
    });
  }
</script>

<template>
  <RouterView v-slot="{ Component, route }">
    <Transition
      name="page-transition"
      appear
      @leave="onLeave"
      @enter="onEnter"
      css="false"
    >
      <component :is="Component" :key="route.path" />
    </Transition>
  </RouterView>
</template>

<style>
  .page-transition-leave-active {
    position: absolute;
  }
</style>
