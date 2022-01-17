<template>
  <div class="l-grid">
    <div class="l-card" v-for="l in licencePlates" :key="l">{{ l }}</div>
  </div>
</template>

<script>
export default {
  name: 'LicencePlate',
  data() {
    return {
      licencePlates: [],
      charSource: [
        ...[...Array(26).keys()].map((i) => String.fromCharCode(i + 65)),
        ...[...Array(26).keys()].map((i) => String.fromCharCode(i + 65)),
        ...[...Array(10).keys()].map((i) => i),
        ...[...Array(10).keys()].map((i) => i),
        ...[...Array(10).keys()].map((i) => i),
        ...[...Array(10).keys()].map((i) => i),
      ],
    };
  },
  created() {
    this.generateNewLicencePlate();
    setInterval(() => {
      this.generateNewLicencePlate();
      this.$nextTick(() => {
        window.scrollTo(0, document.body.scrollHeight);
      });
    }, 120000);
  },
  methods: {
    generateNewLicencePlate() {
      this.licencePlates.push(
        this.charSource
          .sort(() => Math.random() - 0.5)
          .filter((c, i) => i < 6)
          .join('')
      );
    },
  },
};
</script>

<style scoped lang="scss">
.l-grid {
  padding: 16px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  column-gap: 16px;
  row-gap: 16px;
}
.l-card {
  border: solid 1px #cccccc;
  border-radius: 4px;
  padding: 16px;
  font-family: Consolas, monaco, monospace;
  font-size: 180px;
  line-height: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
}
@media (max-width: 600px) {
  .l-grid {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>
