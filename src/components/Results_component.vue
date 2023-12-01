<template>
  <p>reaction time:{{ score }} ms</p>
  <p> {{ rank }}</p>
</template>
<script>
export default {
  props: ['score'],

  data() {
    return {
      rank: null,
    };
  },

  mounted() {
    if (this.score < 250) {
      this.rank = 'Ninga finger';
    } else if (this.score < 400) {
      this.rank = 'Rapid Reflexes ';
    } else {
      this.rank = 'Snail pace...';
    }
  },
};
</script>
<style></style>
