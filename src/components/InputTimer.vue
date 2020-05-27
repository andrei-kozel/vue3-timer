<template>
  <div class="text-center">
    <Title />
    <div class="flex flex-row">
      <BaseInput name="days" @updateState="updateState" />
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <BaseInput name="hours" @updateState="updateState" />
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <BaseInput name="minutes" @updateState="updateState" />
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <BaseInput name="seconds" @updateState="updateState" />
    </div>
    <div
      class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 my-4 rounded "
      v-if="error"
    >
      <strong class="font-bold">Holy smokes! </strong>
      <span class="block sm:inline">Only positive numbers my friend!</span>
      <span class="absolute top-0 bottom-0 right-0 px-4 py-3"> </span>
    </div>
    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-4"
      @click="setState"
    >
      Start timer
    </button>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import { ref, reactive, computed, onMounted, emit } from "vue";
import Title from "./BaseUI/BaseTitle";
import BaseInput from "./BaseUI/BaseInput";
export default {
  components: {
    Title,
    BaseInput
  },
  setup(props, { emit }) {
    const state = reactive({
      days: "",
      hours: "",
      minutes: "",
      seconds: ""
    });
    let error = ref(false);
    const setTimerToTrue = true;
    const setState = () => {
      checkStateIsAnyEmpty(state);
      for (let key in state) {
        if (parseInt(state[key]) && parseInt(state[key]) >= 0) {
          error.value = false;
          emit("setState", { state, setTimerToTrue });
        } else {
          error.value = true;
        }
      }
    };

    const checkStateIsAnyEmpty = state => {
      for (let key in state) {
        if (state[key] < 1 || state[key] === "") {
          state[key] = 0;
        }
      }
    };

    const updateState = e => {
      state[e.key] = e.value;
    };

    return { state, error, setState, updateState };
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
