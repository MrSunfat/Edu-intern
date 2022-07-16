<template>
  <div class="system-page">
    <div class="system-page__control d-flex">
      <div class="left">
        <input-icon />
      </div>
      <div class="right d-flex">
        <base-btn
          nameBtn="Thêm"
          type="primary-btn"
          :handleClick="handleOpenFormAddTeacher"
        />
        <base-btn class="export-icon" nameBtn="Xuất khẩu" type="second-btn" />
        <base-btn :urlIcon="urlMoreIcon" type="icon-btn" />
      </div>
    </div>
    <table-teachers class="system-page__table" />
    <footer-bar-pagination />
    <form-add-teacher
      :class="{ show: !this.closeFormTeacher }"
      v-on:closeFormAddTeacher="handleCloseFormAddTeacher"
    />
    <popup-notify
      :class="{ show: !this.closePopupNotify }"
      v-on:closePopupNotify="handleClosePopupNotify"
    />
  </div>
</template>

<script>
import BaseBtn from "../common/button/BaseBtn.vue";
import InputIcon from "../input/InputIcon.vue";
// icon
import moreIcon from "../../assets/Icons/ic_More.png";
import TableTeachers from "../table/TableTeachers.vue";
import FooterBarPagination from "../footer-bar/FooterBarPagination.vue";
import PopupNotify from "../popup/PopupNotify.vue";
import FormAddTeacher from "../form/FormAddTeacher.vue";
export default {
  name: "SystemPage",
  data() {
    return {
      urlMoreIcon: moreIcon,
      closeFormTeacher: false,
      closePopupNotify: true,
    };
  },
  components: {
    InputIcon,
    BaseBtn,
    TableTeachers,
    FooterBarPagination,
    PopupNotify,
    FormAddTeacher,
  },
  methods: {
    /**
     * Đóng popup thông báo
     * Author: Tran Danh (16/7/2022)
     */
    handleClosePopupNotify() {
      this.closePopupNotify = true;
    },
    /**
     * Đóng form thêm giáo viên
     * Author: Tran Danh (16/7/2022)
     */
    handleCloseFormAddTeacher(data) {
      this.closeFormTeacher = data;
    },
    /**
     * Mở form thêm giáo viên
     * Author: Tran Danh (16/7/2022)
     */
    handleOpenFormAddTeacher() {
      this.closeFormTeacher = false;
    },
  },
};
</script>

<style scoped>
.system-page {
  height: 100%;
  width: 100%;
}

.system-page__control {
  justify-content: space-between;
  margin: 16px 0;
}

.export-icon {
  margin: 0 8px;
}

.system-page__table {
  max-height: calc(
    100% - (var(--height-input) + 24px + var(--height-pagination))
  );
  height: calc(100% - (var(--height-input) + 24px + var(--height-pagination)));
}
</style>