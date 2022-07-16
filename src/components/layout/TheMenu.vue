<template>
  <div class="menu">
    <div class="menu__header d-flex" v-on:click="handleToggleMenu">
      <div class="header__title d-flex" v-on:click="handleToggleMenu">
        <img
          src="../../assets/Icons/ic_IconThietBi.svg"
          alt="thiet-bi-icon"
          class="fs-37 title__icon"
        />
        <h1 class="title title__content">Thiết bị</h1>
      </div>
      <div class="fs-34 toggle-icon"></div>
    </div>
    <div class="menu__list">
      <li v-for="menu in menuList" :key="menu.title">
        <menu-item :title="menu.title" :iconItem="menu.iconItem" />
      </li>
    </div>
  </div>
</template>

<script>
import MenuItem from "../common/menu-item/MenuItem.vue";
// Icon
import OverviewIcon from "../../assets/Icons/ic_TongQuan.svg";
import DeviceIcon from "../../assets/Icons/ic_ThietBi.svg";
import LoanAndPayIcon from "../../assets/Icons/ic_MuonTra.svg";
import SuggestIcon from "../../assets/Icons/ic_DeNghiMuaSam.svg";
import ReportIcon from "../../assets/Icons/ic_BaoCao.svg";
import SystemIcon from "../../assets/Icons/ic_HeThong.svg";

export default {
  name: "TheMenu",
  data() {
    return {
      menuList: [
        { title: "Tổng quan", iconItem: OverviewIcon },
        { title: "Thiết bị", iconItem: DeviceIcon },
        { title: "Mượn trả", iconItem: LoanAndPayIcon },
        { title: "Đề nghị mua sắm", iconItem: SuggestIcon },
        { title: "Hệ thống", iconItem: SystemIcon },
        { title: "Báo cáo", iconItem: ReportIcon },
      ],
    };
  },
  components: {
    MenuItem,
  },
  methods: {
    handleToggleMenu() {
      this.$emit("toggleMenu");
    },
  },
};
</script>

<style scoped>
.menu {
  background-color: var(--bg-menu-sidebar);
  flex-direction: column;
}

/* header */
.menu__header {
  padding: 10px 3px 10px 12px;
  width: 100%;
  justify-content: space-between;
  height: var(--height-menu-header);
}

.menu__header .header__title {
  justify-content: space-between;
}

.menu__header .title__content {
  color: var(--header-title-on-sidebar);
  margin-left: 8px;
}

.menu__header .toggle-icon {
  background-image: url("../../assets/Icons/ic_sprites.svg");
  background-repeat: no-repeat;
  background-position: -9px -8px;
  cursor: pointer;
}

/* list */
.menu__list {
  /* padding-left: 12px; */
  margin-top: 9px;
}

.menu__list li {
  list-style-type: none;
}

/* .menu__list li {
    margin-bottom: 13px;
} */

/* no expand */
.menu.no-expand {
}

.menu.no-expand .menu__header {
}

#app.menu-no-expand .menu .header__title {
  display: none;
}

#app.menu-no-expand .menu .menu__item__title {
  display: none;
}

#app.menu-no-expand .menu__header .toggle-icon {
  background-position: -12px -8px;
}
</style>