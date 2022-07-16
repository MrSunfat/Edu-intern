<template>
    <div class="toast-success toast-messager d-flex">
        <div class="toast-success__icon">
            <img src="../../assets/Icons/ic_ToastMessage_Success.png" alt="" class="toast-success__icon-img">
        </div>
        <div class="toast-success__main">
            <h1 class="title toast-success__title mg-bt-8">Thành công</h1>
            <p class="subtitle-two">Đã gửi thông báo cho phụ huynh</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "ToastSuccess"
}
</script>

<style>
.toast-success {
    position: fixed;
    top: 10px;
    right: 0;
    border-left: 5px solid var(--main-color);
}

.toast-success__icon {
    margin-right: 18px;
}

</style>