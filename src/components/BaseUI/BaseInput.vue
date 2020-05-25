/* eslint-disable no-unused-vars */
<template>
  <section class="flex flex-col items-center container">
    <span class="flex justify-center items-center text-6xl leading-none container-numbers">
      <input
        type="text"
        maxlength="2"
        class="rounded-lg text-center focus:outline-none focus:shadow-outline text-transparent"
        @keyup="update"
        v-model="state.value"
      />
    </span>
    <p class="tracking-wider font-hairline mt-1">{{ name }}</p>
  </section>
</template>

<script>
/* eslint-disable no-unused-vars */
import { ref, reactive, emit } from "vue";
export default {
  props: {
    name: { type: String, required: true }
  },
  setup(props, { emit }) {
    const state = reactive({
      value: "",
      key: props.name
    });

    const update = e => {
      emit("updateState", { ...state });
    };

    return { state, update };
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
