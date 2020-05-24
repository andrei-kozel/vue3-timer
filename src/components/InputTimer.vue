<template>
  <div class="text-center">
    <h1 class="text-2xl">Don’t use a smoke alarm as a reminder.</h1>
    <h1 class="mb-8 text-2xl">Use this one!</h1>
    <div class="flex flex-row">
      <section class="flex flex-col items-center container">
        <span class="flex justify-center items-center text-6xl leading-none container-numbers">
          <input
            type="text"
            maxlength="2"
            class="rounded-lg text-center focus:outline-none focus:shadow-outline text-transparent"
            v-model="state.days"
          />
        </span>
        <p class="tracking-wider font-hairline mt-1">days</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <section class="flex flex-col items-center container">
        <span class="flex justify-center items-center text-6xl leading-none container-numbers">
          <input
            v-model="state.hours"
            type="text"
            maxlength="2"
            class="rounded-lg text-center focus:outline-none focus:shadow-outline text-transparent"
          />
        </span>
        <p class="tracking-wider font-hairline mt-1">hours</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <section class="flex flex-col items-center container">
        <span class="flex justify-center items-center text-6xl leading-none container-numbers">
          <input
            v-model="state.minutes"
            type="text"
            maxlength="2"
            class="rounded-lg text-center focus:outline-none focus:shadow-outline text-transparent"
          />
        </span>
        <p class="tracking-wider font-hairline mt-1">minutes</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <section class="flex flex-col items-center container">
        <span class="flex justify-center items-center text-6xl leading-none container-numbers">
          <input
            v-model="state.seconds"
            type="text"
            maxlength="2"
            class="rounded-lg text-center focus:outline-none focus:shadow-outline text-transparent"
          />
        </span>
        <p class="tracking-wider font-hairline mt-1">seconds</p>
      </section>
    </div>
    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-8"
      @click="setState"
    >Start timer</button>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import { reactive, computed, onMounted, emit } from "vue";
export default {
  setup(props, { emit }) {
    const state = reactive({
      days: "",
      hours: "",
      minutes: "",
      seconds: ""
    });
    const setTimerToTrue = true;
    const setState = () => {
      emit("setState", { state, setTimerToTrue });
    };
    return { state, setState };
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

input {
  height: 70px;
  width: 90px;
  text-shadow: 0 0 0 #2d3748;
}
</style>
