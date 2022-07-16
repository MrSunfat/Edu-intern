<template>
  <div class="popup-notify-overlay">
    <div class="popup-notify">
      <h1 class="title popup-notify__title">{{ titleNotify }}</h1>
      <p class="subtitle-one">{{ contentNotify }}</p>
      <div class="popup-notify__btns mg-t-16">
        <base-btn
          class="close-btn"
          nameBtn="Đóng"
          type="second-btn"
          :handleClick="handleClosePopupNotify"
        />
        <base-btn
          class="access-btn mg-l-8"
          nameBtn="Xác nhận"
          type="primary-btn"
        />
      </div>
      <div class="popup-notify__close c-p" @click="handleClosePopupNotify">
        <img src="../../assets/Icons/ic_X_2.png" alt="" class="close-icon" />
      </div>
    </div>
  </div>
</template>

<script>
import BaseBtn from "../common/button/BaseBtn.vue";
export default {
  name: "PopupNotify",
  props: {
    titleNotify: {
      type: String,
      default: "Thông báo",
    },
    contentNotify: {
      type: String,
      default: "Bạn có chắc chắn xóa Cán bộ, giáo viên đang chọn không ?",
    },
  },
  components: { BaseBtn },
  methods: {
    handleClosePopupNotify() {
      this.$emit("closePopupNotify", true);
    },
  },
};
</script>

<style scoped>
.popup-notify-overlay {
  position: fixed;
  background-color: rgba(0, 0, 0, 0.85);
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: none;
}

.popup-notify-overlay.show {
  display: flex;
  align-items: center;
}

.popup-notify {
  position: relative;
  width: 400px;
  background-color: #fff;
  margin: 0 auto;
  padding: 20px 24px;
  border-radius: 4px;
}

.popup-notify__title {
  font-size: 22px !important;
  margin-bottom: 12px;
}

.popup-notify__btns {
  text-align: right;
}

.popup-notify__close {
  position: absolute;
  top: 5px;
  right: 5px;
}
</style>