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
    {{ state.showError }}
    <div v-if="state.errors > 0">Error</div>
    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-8"
      @click="setState"
    >Start timer</button>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import { reactive, computed, onMounted, emit } from "vue";
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
      seconds: "",
      errors: 0
    });
    const setTimerToTrue = true;
    const setState = () => {
      checkStateIsAnyEmpty(state);
      emit("setState", { state, setTimerToTrue });
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

    return { state, setState, updateState };
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
