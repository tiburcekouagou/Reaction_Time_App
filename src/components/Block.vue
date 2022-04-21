<template>
  <div class="flex justify-center items-center bg-green-800 rounded-xl text-white w-2/3 md:w-1/4 lg:w-2/4 h-48 md:h-72 text-center mx-auto cursor-pointer" v-if="showBlock" @click="stopTimer">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-20 w-20 animate-bounce" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
      <path stroke-linecap="round" stroke-linejoin="round" d="M14.828 14.828a4 4 0 01-5.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>
  </div>
</template>

<script>
export default {
  name: "Block",
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
  mounted() {
    console.log("Component Mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  updated() {
    console.log("The componenet take %f ms to show", this.delay);
    console.log("Component Updated");
  },
  unmounted() {
    console.log("Component unmounted");
  },
  props: ["delay"],
};
</script>
