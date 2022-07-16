<template>
  <div class="toast-success-two toast-messager-two d-flex show">
    <div class="toast-success-two__icon d-flex">
      <img
        src="../../assets/Icons/ic_ToastMessage_Success.png"
        alt=""
        class="toast-success__icon-img"
      />
    </div>
    <div class="toast-success-two__main">
      <h1 class="title toast-success-two__title mg-bt-8">Thành công</h1>
      <p class="subtitle-two">Đã gửi thông báo cho <span class="link c-p">phụ huynh</span></p>
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
  name: "ToastSuccessTwo",
};
</script>

<style>
.toast-success-two {
  position: fixed;
  top: 10px;
  right: 0;
  border-left: 5px solid var(--main-color);
  padding-right: 8px;
}

.toast-success-two__icon {
  margin-right: 15px;
}

.toast-messager__close {
  margin-left: 30px;
}

.link {
    color: var(--link-color);
}
</style>