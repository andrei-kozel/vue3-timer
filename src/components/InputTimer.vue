<template>
  <div class="flex flex-col bg-green-200 justify-center items-center h-full ">
    <h1 class="text-2xl mb-8">Don’t use a smoke alarm as a reminder.</h1>

    <div class="flex flex-row">
      <section class="flex flex-col items-center container">
        <span
          class="flex justify-center items-center text-6xl leading-none container-numbers  "
        >
          <input
            type="text"
            maxlength="2"
            class="rounded-lg text-center focus:outline-none focus:shadow-outline text-transparent"
          />
        </span>
        <p class="tracking-wider font-hairline mt-1">days</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <section class="flex flex-col items-center container">
        <span
          class="flex justify-center items-center text-6xl leading-none container-numbers  "
        >
          <input
            type="text"
            maxlength="2"
            class="rounded-lg text-center focus:outline-none focus:shadow-outline text-transparent"
          />
        </span>
        <p class="tracking-wider font-hairline mt-1">hours</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <section class="flex flex-col items-center container">
        <span
          class="flex justify-center items-center text-6xl leading-none container-numbers  "
        >
          <input
            type="text"
            maxlength="2"
            class="rounded-lg text-center focus:outline-none focus:shadow-outline text-transparent"
          />
        </span>
        <p class="tracking-wider font-hairline mt-1">minutes</p>
      </section>
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <section class="flex flex-col items-center container">
        <span
          class="flex justify-center items-center text-6xl leading-none container-numbers  "
        >
          <input
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
    >
      Start timer
    </button>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import { reactive, computed, onMounted } from "vue";
export default {
  setup() {}
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
  width: 90px;
  text-shadow: 0 0 0 #2d3748;
}
</style>
