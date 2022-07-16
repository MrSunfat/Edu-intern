<template>
  <div class="dropdown-one" :class="{ binding: binding }">
    <label for="dropdown-one" class="subtitle-two d-flex">
      {{ label }}<span style="color: red">*</span>
    </label>
    <div
      id="dropdown-one"
      class="ip-default dropdown-one__container d-flex"
      @click="handleOpenDropdown"
    >
      <h1 class="subtitle-two content">{{ dbDropdown.optionSelected }}</h1>
      <div class="dropdown-one__down-icon">
        <img src="../../assets/Icons/ic_Chevron.png" alt="" class="down-icon" />
      </div>
    </div>
    <ul class="dropdown-one__options" :class="this.openDropdown && 'show'">
      <li
        class="dropdown-one__option d-flex"
        :class="{ selected: option.selected }"
        v-for="option in dbDropdown.listSubjectGroup"
        :key="option.name"
        @click="chooseOption(option.name)"
      >
        {{ option.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "DropDownOne",
  props: {
    label: String,
    binding: Boolean,
    dbDropdown: Object,
  },
  data() {
    return {
      openDropdown: false,
    };
  },
  methods: {
    /*
      Mở các option
      Author: Tran Danh (16/7/2022)
    */
    handleOpenDropdown() {
      this.openDropdown = !this.openDropdown;
    },
    /**
     * Đóng các option
     * Author: Tran Danh (16/7/2022)
     */
    handleCloseOption() {
      this.openDropdown = false;
    },
    /**
     * Truyền tên option và kích hoạt sự kiện -> chọn option
     * Author: Tran Danh (16/7/2022)
     */
    chooseOption(nameOption) {
      this.$emit("changeOption", nameOption);
      this.handleCloseOption();
    },
  },
  computed: {},
};
</script>

<style>
.dropdown-one {
  display: grid;
  grid-template-columns: var(--width-title-h-input) calc(
      100% - var(--width-title-h-input)
    );
  position: relative;
  margin-bottom: 12px;
}

.dropdown-one label.subtitle-two > span {
  display: none;
}

.dropdown-one.binding label.subtitle-two > span {
  display: block;
}

.dropdown-one__container {
  justify-content: space-between;
  padding-left: 12px;
  margin-left: 12px;
  cursor: pointer;
}

.dropdown-one__container > .content {
  padding: 0;
  color: var(--main-color-in-form);
}

.dropdown-one__down-icon {
  margin: 0 12px;
}

/* option */

.dropdown-one__options {
  position: absolute;
  content: "";
  top: calc(var(--height-input) + 5px);
  /* left: 0; */
  right: 0;
  padding-left: 0;
  padding-top: 4px;
  padding-bottom: 4px;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 0 5px #b1b1b1;
  overflow: hidden;
  z-index: 2;
  width: calc(100% - var(--width-title-h-input) - 12px);
  max-height: 125px;
  overflow-y: scroll;
  display: none;
}

.dropdown-one__options::-webkit-scrollbar {
  width: 5px;
}

.dropdown-one__options::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px #e5e5e5;
  border-radius: 4px;
}

.dropdown-one__options::-webkit-scrollbar-thumb {
  background: #bbb;
  border-radius: 4px;
}

.dropdown-one__options.show {
  display: block;
}

.dropdown-one__option {
  list-style-type: none;
  height: var(--height-option-dropdown);
  padding-left: 16px;
  color: var(--main-color-in-form);
}

.dropdown-one__option:hover {
  background: var(--hover-color);
  cursor: pointer;
}

.dropdown-one__option.selected {
  background: var(--row-focus-color-on-grid-color);
}
</style>