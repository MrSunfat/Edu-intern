<template>
  <div
    class="base-toast toast-messager d-flex"
    :class="typeToast"
    v-if="!closeToast"
  >
    <div class="base-toast__icon">
      <img :src="handleTypeIconToast" alt="" class="base-toast__icon-img" />
    </div>
    <div class="base-toast__main">
      <h1 class="title base-toast__title mg-bt-8">{{ titleToast }}</h1>
      <p class="subtitle-two">
        {{ this.contentToast }}
        <a
          :href="this.linkToast.urlLink"
          class="link-text c-p"
          v-show="isHaveLinkToast"
          >{{ this.linkToast.title }}</a
        >
      </p>
    </div>
    <div
      class="toast-messager__close d-flex c-p"
      v-show="isHaveLinkToast"
      @click="isCloseToast"
    >
      <img
        src="../../assets/Icons/ic_X_40.png"
        alt=""
        class="toast-messager__close-img"
      />
    </div>
  </div>
</template>

<script>
// icon toast
import successIcon from "../../assets/Icons/ic_ToastMessage_Success.png";
import failIcon from "../../assets/Icons/ic_ToastMessage_Fail.png";
import warnIcon from "../../assets/Icons/ic_ToastMessage_Warning.png";
import infoIcon from "../../assets/Icons/ic_ToastMessage_Info.png";

export default {
  name: "BaseToast",
  props: {
    titleToast: {
      type: String,
      default: "Thông báo",
    },
    contentToast: {
      type: String,
      default: "Đã thành công",
    },
    linkToast: {
      type: Object,
      default: () => ({
        title: "Đã thành công",
        urlLink: "",
      }),
    },
    typeToast: {
      type: String,
      default: "toast-success",
    },
  },
  data() {
    return {
      closeToast: false,
    };
  },
  methods: {
    /**
     * Đóng toast message
     * Author: Tran Danh (17/7/2022)
     */
    isCloseToast() {
      this.closeToast = true;
    },
  },
  computed: {
    /**
     * Xử lý các thể loại toast message -> icon toast
     * Author: Tran Danh (17/7/2022)
     */
    handleTypeIconToast() {
      switch (this.typeToast) {
        case "toast-success":
          return successIcon;
        case "toast-fail":
          return failIcon;
        case "toast-warning":
          return warnIcon;
        case "toast-info":
          return infoIcon;
        default:
          return successIcon;
      }
    },
    /**
     * Xét việc show link toast và show delete icon
     * Author: Tran Danh (17/7/2022)
     */
    isHaveLinkToast() {
      return this.linkToast.title ? true : false;
    },
  },
  mounted() {
    setTimeout(
      () => {
        this.isCloseToast();
        console.log(this.linkToast);
      },
      this.linkToast.title ? 5000 : 3000
    );
  },
};
</script>

<style scoped>
.base-toast {
  position: fixed;
  top: 10px;
  right: 5px;
  border-left: 5px solid var(--main-color);
}

.base-toast__icon {
  margin-right: 18px;
}

/* success */
.toast-success {
  border-left: 5px solid var(--main-color);
}

/* fail */
.toast-fail {
  border-left: 5px solid var(--hover-delete-icon-color);
}

/* warning */
.toast-warning {
  border-left: 5px solid var(--warn-color);
}

/* info */
.toast-info {
  position: fixed;
  top: 120px;
  right: 0px;
  border-left: 5px solid var(--link-color);
}

/* toast messager default */
.toast-messager {
  min-height: 80px;
  min-width: 300px;
  background-color: #fff;
  box-shadow: 0 0 5px #b1b1b1;
  border-radius: 4px;
  padding: 8px 18px 7px 15px;
  /* right: -350px; */
}

.toast-messager.show {
  right: 16px;
}

.toast-messager__close {
  margin-left: 30px;
  margin-right: -10px;
}

.link-text {
  text-decoration: none;
  color: var(--link-color);
}
</style>