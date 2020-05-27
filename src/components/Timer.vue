<template>
  <div class="text-center">
    <Title />
    <div class="flex flex row text-gray-700" v-if="!state.finished">
      <TimerCard :time="state.days" name="days" :isLoaded="state.loaded" />
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <TimerCard :time="state.hours" name="hours" :isLoaded="state.loaded" />
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <TimerCard
        :time="state.minutes"
        name="minutes"
        :isLoaded="state.loaded"
      />
      <section class="text-4xl leading-relaxed mx-3">:</section>

      <TimerCard
        :time="state.seconds"
        name="seconds"
        :isLoaded="state.loaded"
      />
    </div>
    <div v-else>
      <h1 class="text-3xl text-purple-600">Time waits for no one.</h1>
    </div>

    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-8"
      @click="$emit('setStatus', false)"
    >
      <div>Stop timer</div>
    </button>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import { reactive, computed, onMounted, emit } from "vue";
import TimerCard from "./BaseUI/BaseTimerCard";
import Title from "./BaseUI/BaseTitle";

export default {
  props: {
    propState: Object
  },
  components: {
    TimerCard,
    Title
  },
  setup(props) {
    const state = reactive({
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
      loaded: false,
      finished: false
    });

    const _seconds = 1000;
    const _minutes = computed(() => _seconds * 60);
    const _hours = computed(() => _minutes.value * 60);
    const _days = computed(() => _hours.value * 24);
    const end = computed(
      () =>
        new Date(
          new Date().getFullYear(),
          new Date().getMonth(),
          new Date().getDate() + parseInt(props.propState.days),
          new Date().getHours() + parseInt(props.propState.hours),
          new Date().getMinutes() + parseInt(props.propState.minutes),
          new Date().getSeconds() + parseInt(props.propState.seconds)
        )
    );

    const formatTime = num => (num < 10 ? "0" + num : num);

    const setCoundDown = () => {
      const timer = setInterval(() => {
        const now = new Date();
        const distance = end.value.getTime() - now.getTime();

        if (distance < 0) {
          clearInterval(timer);
          state.finished = true;
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
        state.loaded = true;
      }, 1000);
    };

    onMounted(() => {
      setCoundDown();
    });

    return { state };
  }
};
/* eslint-enable no-unused-vars */
</script>
