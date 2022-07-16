<template>
  <div class="btn-style-three i-d-flex">
    <button class="reset-btn btn-main">{{ nameBtn }}</button>
    <button class="reset-btn selector">
      <div class="down-icon"></div>
    </button>
  </div>
</template>

<script>
export default {
  name: "BtnStyleThree",
  props: {
    nameBtn: String,
  },
};
</script>

<style scoped>
@import url("../../../style/components/button/btn-style-three.css");
</style>