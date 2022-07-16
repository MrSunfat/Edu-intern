<template>
  <div class="h-label-input" :class="{ binding: binding }">
    <div class="notify d-flex">{{ errorNotify }}</div>
    <div class="arrow-down"></div>
    <label :for="label" class="subtitle-two d-flex">
      {{ label }} <span style="color: red">*</span>
    </label>
    <input
      :id="label"
      :tabindex="tabindex"
      type="text"
      placeholder=""
      class="ip-default h-label-input__main"
      :ref="stringRef"
    />
  </div>
</template>

<script>
export default {
  name: "HLabelInput",
  props: {
    label: String,
    binding: Boolean,
    tabindex: Number,
    stringRef: String,
  },
  mounted() {
    if (this.tabindex === 1) {
      this.focusInput();
    }
  },
  methods: {
    focusInput() {
      console.log("Hello");
      this.$refs.firstFocus.focus();
    },
  },
  computed: {
    errorNotify() {
      return `${this.label} không được bỏ trống !`;
    },
  },
};
</script>

<style scoped>
.h-label-input {
  position: relative;
  display: grid;
  grid-template-columns: var(--width-title-h-input) calc(
      100% - var(--width-title-h-input)
    );
  margin-bottom: 12px;
  min-width: 100%;
  height: var(--height-input);
}

.h-label-input.binding.error .notify {
  --height-notify: 22px;
  position: absolute;
  content: "";
  top: calc(-5px - var(--height-notify));
  left: 0;
  right: 0;
  background-color: var(--hover-delete-icon-color);
  color: #fff;
  /* text-align: center; */
  border-radius: 4px;
  height: var(--height-notify);
  font-size: 12px;
  /* align-content: center; */
  justify-content: center;
  display: flex;
}

.h-label-input.binding.error .arrow-down {
  position: absolute;
  top: -5px;
  right: 50px;
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent; 
  border-top: 5px solid var(--hover-delete-icon-color);
  display: block;
}

.h-label-input .notify {
  display: none;
}

.h-label-input .arrow-down {
  display: none;
}

.h-label-input h1 {
  line-height: 0;
}

.h-label-input span {
  display: none;
}

.h-label-input.binding span {
  display: block;
}

.h-label-input.binding h1 {
  line-height: 100%;
}

.h-label-input.error > .h-label-input__main {
  border-color: var(--hover-delete-icon-color);
}

.h-label-input__main {
  min-width: 135px;
  margin-left: 12px;
  padding: 0 12px;
}
</style>