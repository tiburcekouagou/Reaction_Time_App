<template>
  <p class="text-center">
    Temps de reaction : <span class="font-bold text-xl text-amber-600">{{ score }}</span
    >ms
  </p>
  <div v-if="score < 100">
    <ThumbsUp />
  </div>
  <div v-else>
    <ThumbsDown />
  </div>
</template>

<script>
import ThumbsUp from "./ThumbsUp.vue";
import ThumbsDown from "./ThumbsDown.vue";
export default {
  name: "Results",
  props: ["score"],
  components: { ThumbsUp, ThumbsDown },
};
</script>
