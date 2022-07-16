<template>
  <div class="footer__standard d-flex">
    <div class="standard__total fs-t-14 d-flex">
      Tổng: &nbsp;
      <h1 class="title fs-t-14">40 học sinh</h1>
    </div>
    <div class="standard__btns">
      <btn-style-two nameBtn="Quay lại" class="btn__back" />
      <btn-style-one nameBtn="Lưu" class="btn__save" />
    </div>
  </div>
</template>

<script>
import BtnStyleOne from "../common/button/BtnStyleOne.vue";
import BtnStyleTwo from "../common/button/BtnStyleTwo.vue";
export default {
  components: { BtnStyleTwo, BtnStyleOne },
  name: "FooterBarStandard",
};
</script>

<style>
@import url("../../style/components/footer/footer-bar-standard.css");
</style>