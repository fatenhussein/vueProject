<template>
  <div class="block" v-if="showBlock" @click="stopTimer">clcke me</div>
</template>
<script>
export default {
  props: ['delay'],

  data() {
    return {
      showBlock: false,

      timer: null,

      reactionTime: 0,
    };
  },

  mounted() {
    console.log('componet mounted ');

    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },

  updated() {
    console.log('component updated');
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime = this.reactionTime+ 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);

      console.log(this.reactionTime);

      this.$emit('end'  ,this.reactionTime)
    },
  },
};
</script>
<style>
.block {
  width: 400px;

  border-radius: 20px;

  background-color: aquamarine;
  color: white;

  text-align: center;
  padding: 100px 0px;

  margin: 40px auto;
}
</style>
