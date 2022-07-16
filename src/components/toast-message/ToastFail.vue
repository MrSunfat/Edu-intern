<template>
    <div class="toast-fail toast-messager d-flex">
        <div class="toast-fail__icon">
            <img src="../../assets/Icons/ic_ToastMessage_Fail.png" alt="" class="toast-fail__icon-img">
        </div>
        <div class="toast-fail__main">
            <h1 class="title toast-fail__title mg-bt-8">Lỗi</h1>
            <p class="subtitle-two">Error Message</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "ToastFail"
}
</script>

<style>
.toast-fail {
    position: fixed;
    top: 50px;
    right: 0px;
    border-left: 5px solid var(--hover-delete-icon-color);
}

.toast-fail__icon {
    margin-right: 18px;
}

</style>