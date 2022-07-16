<template>
    <div class="toast-info toast-messager d-flex">
        <div class="toast-info__icon">
            <img src="../../assets/Icons/ic_ToastMessage_Info.png" alt="" class="toast-info__icon-img">
        </div>
        <div class="toast-info__main">
            <h1 class="title toast-info__title mg-bt-8">Cảnh báo</h1>
            <p class="subtitle-two">info Message</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "ToastInfo"
}
</script>

<style>
.toast-info {
    position: fixed;
    top: 120px;
    right: 0px;
    border-left: 5px solid var(--link-color);
}

.toast-info__icon {
    margin-right: 18px;
}

</style>