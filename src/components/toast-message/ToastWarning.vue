<template>
    <div class="toast-warning toast-messager d-flex">
        <div class="toast-warning__icon">
            <img src="../../assets/Icons/ic_ToastMessage_Warning.png" alt="" class="toast-warning__icon-img">
        </div>
        <div class="toast-warning__main">
            <h1 class="title toast-warning__title mg-bt-8">Cảnh báo</h1>
            <p class="subtitle-two">Warning Message</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "ToastWarning"
}
</script>

<style>
.toast-warning {
    position: fixed;
    top: 120px;
    right: 0px;
    border-left: 5px solid var(--warn-color);
}

.toast-warning__icon {
    margin-right: 18px;
}

</style>