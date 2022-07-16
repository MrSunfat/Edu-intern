<template>
  <div class="toast-fail-two toast-messager-two d-flex show">
    <div class="toast-fail-two__icon d-flex">
      <img
        src="../../assets/Icons/ic_ToastMessage_Fail.png"
        alt=""
        class="toast-fail__icon-img"
      />
    </div>
    <div class="toast-fail-two__main">
      <h1 class="title toast-fail-two__title mg-bt-8">Thành công</h1>
      <p class="subtitle-two">
        Đã gửi thông báo cho <span class="link c-p">phụ huynh</span>
      </p>
    </div>
    <div class="toast-messager__close d-flex c-p">
      <img
        src="../../assets/Icons/ic_X_40.png"
        alt=""
        class="toast-messager__close-img"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "ToastFailTwo",
};
</script>

<style>
.toast-fail-two {
  position: fixed;
  top: 10px;
  right: 0;
  border-left: 5px solid var(--hover-delete-icon-color);
  padding-right: 8px;
}

.toast-fail-two__icon {
  margin-right: 15px;
}

.toast-messager__close {
  margin-left: 30px;
}

.link {
  color: var(--link-color);
}
</style>