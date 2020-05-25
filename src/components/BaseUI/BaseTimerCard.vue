<template>
  <section class="flex flex-col items-center container">
    <div
      class="flex justify-center items-center text-6xl leading-none container-numbers bg-white bg-opacity-50 rounded-lg"
    >
      <span v-if="isLoaded">{{ time }}</span>
    </div>
    <p class="tracking-wider font-hairline mt-1">{{ name }}</p>
  </section>
</template>

<script>
export default {
  props: {
    time: { type: [Number, String], required: true },
    name: { type: String, required: true },
    isLoaded: { type: Boolean, required: true }
  }
};
</script>

<style scoped>
.container-numbers {
  width: 90px;
  height: 70px;
  text-align: center;
}
</style>
