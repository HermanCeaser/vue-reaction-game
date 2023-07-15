<template>
  <div>
    <p class="block">Reaction Time: {{ results }} ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ["results"],
  data() {
    return {
      rank: "",
    };
  },
  mounted() {
    if (this.results < 250) {
      this.rank = "Ninja Fingers 🚀";
    } else if (this.results < 400) {
      this.rank = "Rapid reflexes 🤗";
    } else {
      this.rank = "Sluggish Pace 😠";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.4rem;
  color: #0fa44f;
  font-weight: 700;
}
</style>
