<template>
  <span class="title">{{ title }}</span>
</template>

<script lang="js">
export default {
  name: 'GradientTitle',
  props: {
    title: {
      type: String,
      required: true,
    }
  },
  setup() {},
}
</script>

<style scoped>
.title {
  font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
  font-size: 3rem;
  font-weight: bold;
  letter-spacing: 2px;
  text-align: center;
  color: #f35626;
  background-image: -webkit-linear-gradient(92deg, #f80000, #00aeff);
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: hue 10s infinite linear;
}
</style>
