<template>
  <div class="flex flex-col bg-green-200 justify-center items-center h-full ">
    <h1 class="text-2xl">Don’t use a smoke alarm as a reminder.</h1>
    <h1 class=" mb-8 text-2xl">Use this one!</h1>
    <div class="flex flex row">
      <section class="flex flex-col items-center container">
        <span
          class="flex justify-center items-center text-6xl leading-none container-numbers bg-white bg-opacity-50 rounded-lg "
          >{{ state.days }}</span
        >
        <p class="tracking-wider font-hairline">days</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <section class="flex flex-col items-center container">
        <span
          class="flex justify-center items-center text-6xl leading-none container-numbers bg-white bg-opacity-50 rounded-lg "
          >{{ state.hours }}</span
        >
        <p class="tracking-wider font-hairline">hours</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <section class="flex flex-col items-center container">
        <span
          class="flex justify-center items-center text-6xl leading-none container-numbers bg-white bg-opacity-50 rounded-lg "
          >{{ state.minutes }}</span
        >
        <p class="tracking-wider font-hairline">minutes</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>
      <section class="flex flex-col items-center container">
        <span
          class="flex justify-center items-center text-6xl leading-none container-numbers bg-white bg-opacity-50 rounded-lg "
          >{{ state.seconds }}</span
        >
        <p class="tracking-wider font-hairline">seconds</p>
      </section>
    </div>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import { reactive, computed, onMounted } from "vue";
export default {
  setup() {
    const state = reactive({
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0
    });
    const _seconds = 1000;
    const _minutes = computed(() => _seconds * 60);
    const _hours = computed(() => _minutes.value * 60);
    const _days = computed(() => _hours.value * 24);

    const formatTime = num => (num < 10 ? "0" + num : num);

    function setCoundDown() {
      const timer = setInterval(() => {
        const now = new Date();
        const end = new Date(2020, 4, 25, 11, 22, 33);
        const distance = end.getTime() - now.getTime();

        if (distance < 0) {
          clearInterval(timer);
          return;
        }

        const days = Math.floor(distance / _days.value);
        const hours = Math.floor((distance % _days.value) / _hours.value);
        const minutes = Math.floor((distance % _hours.value) / _minutes.value);
        const seconds = Math.floor((distance % _minutes.value) / _seconds);

        state.days = days;
        state.hours = formatTime(hours);
        state.minutes = formatTime(minutes);
        state.seconds = formatTime(seconds);
      }, 1000);
    }

    onMounted(() => {
      setCoundDown();
    });

    return { state };
  }
};
/* eslint-enable no-unused-vars */
</script>

<style lang="scss">
.container {
  &-numbers {
    width: 90px;
    height: 70px;
    text-align: center;
  }
}
</style>
