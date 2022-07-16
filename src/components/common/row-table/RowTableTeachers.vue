<template>
  <tr :class="this.teacher.checked && 'checked'">
    <td class="subtitle-one">
      <button
        class="checkbox-input d-flex"
        :class="this.teacher.checked && 'active'"
        v-on:click="handleToggleChecked"
      >
        <img
          src="../../../assets/Icons/ic_Checkbox_Inactive.png"
          alt="checkbox-icon"
          class="checkbox-input__icon"
        />
        <img
          src="../../../assets/Icons/ic_Checkbox_Hover.png"
          alt="checkbox-icon"
          class="checkbox-input__icon-hover"
        />
        <img
          src="../../../assets/Icons/ic_Checkbox_Active.png"
          alt="checkbox-icon"
          class="checkbox-input__icon-checked"
        />
      </button>
    </td>
    <td class="btn center-text">
      {{ teacher.code }}
    </td>
    <td class="btn name-teacher">
      {{ teacher.fullName }}
    </td>
    <td class="btn">
      {{ teacher.phone }}
    </td>
    <td class="subtitle-one">
      {{ teacher.group }}
    </td>
    <td class="subtitle-one">
      {{ teacher.subject }}
    </td>
    <td class="subtitle-one">
      {{ teacher.lab }}
    </td>
    <td class="subtitle-one">
      <div class="check" :class="teacher.training && 'show'">
        <img
          src="../../../assets/Icons/ic_Check.png"
          alt="check-icon"
          class="check__icon"
        />
      </div>
    </td>
    <td class="subtitle-one">
      <div class="check" :class="teacher.jobStatus && 'show'">
        <img
          src="../../../assets/Icons/ic_Check.png"
          alt="check-icon"
          class="check__icon"
        />
      </div>
    </td>
    <td class="subtitle-one">
      <div class="edit-and-delete-info-teacher d-flex">
        <div class="edit__container fs-28 d-flex">
          <img
            src="../../../assets/Icons/ic_Edit.png"
            alt="check-icon"
            class="edit__icon"
          />
        </div>
        <div class="delete__container fs-28 d-flex">
          <img
            src="../../../assets/Icons/ic_Remove.png"
            alt="check-icon"
            class="remove__icon"
          />
          <img
            src="../../../assets/Icons/ic_Remove_Hover.png"
            alt="check-icon"
            class="remove__icon-hover"
          />
        </div>
      </div>
    </td>
  </tr>
</template>

<script>
export default {
  name: "RowTableTeachers",
  data() {
    return {
      // rowChecked: false,
    };
  },
  props: {
    teacher: Object,
  },
  methods: {
    /*
      - Kích hoạt sự kiện `toggelChecked` và đẩy dữ liệu lên 
      -> TableTeachers.vue : nhận sự kiện + dữ liệu -> xử lý
      - Kích hoạt sự kiện `checkORunchekAuto` 
      -> nút checkALL auto check hoặc uncheck
    */
    handleToggleChecked() {
      this.$emit("toggelChecked", this.teacher.code);
    },
  },
  computed: {},
};
</script>

<style scoped>
/* checkbox */
.checkbox-input {
    border: none;
    cursor: pointer;
    background-color: transparent;
}

.checkbox-input__icon-hover, .checkbox-input__icon-checked {
    display: none;
}

.checkbox-input:hover .checkbox-input__icon {
    display: none;
}

.checkbox-input:hover .checkbox-input__icon-hover {
    display: block;
}

.checkbox-input.active .checkbox-input__icon {
    display: none;
}

.checkbox-input.active .checkbox-input__icon-hover {
    display: none;
}

.checkbox-input.active .checkbox-input__icon {
    display: none;
}

.checkbox-input.active .checkbox-input__icon-checked {
    display: block;
}

tr .check {
    text-align: center;
}

tr:hover {
    background-color: var(--hover-color) !important;
}

tr.checked {
    background-color: var(--row-focus-color-on-grid-color) !important;
}

.name-teacher {
    color: var(--main-color);
}

/* icon */
.edit__container {
    justify-content: center;
}

.edit__container:hover, .delete__container:hover {
    background-color: var(--bg-icon-hover);
    border-radius: 50%;
}
</style>