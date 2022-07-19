<template>
  <div class="tag-comp i-d-flex">
    <div class="label subtitle-two">{{ label }}</div>
    <div class="container ip-default i-d-flex">
      <div class="tag-comp__main d-flex">
        <div
          class="tag__option d-flex"
          v-for="subject in listSubject"
          :key="subject.id"
          v-show="subject.selected"
        >
          <h1 class="content subtitle-two d-flex">{{ subject.name }}</h1>
          <div class="delete__option c-p">
            <img
              :src="deleteIconUrl"
              alt=""
              @click="deleteSubject(subject.id)"
            />
          </div>
        </div>
        <input type="text" class="main__input" @click="handleShowListSubject" />
      </div>
      <div class="tag-comp__second d-flex c-p" @click="handleShowListSubject">
        <img :src="downIconUrl" alt="" class="down-icon" />
      </div>
      <ul class="list-student" :class="{ show: this.showListSubject }">
        <li class="list-title d-flex">
          <button
            class="checkbox-input d-flex mg-r-8"
            :class="{ active: this.checkAll }"
            @click="handleCheckAll"
          >
            <img
              src="../../assets/Icons/ic_Checkbox_Inactive.png"
              alt="checkbox-icon"
              class="checkbox-input__icon"
            />
            <img
              src="../../assets/Icons/ic_Checkbox_Hover.png"
              alt="checkbox-icon"
              class="checkbox-input__icon-hover"
            />
            <img
              src="../../assets/Icons/ic_Checkbox_Active.png"
              alt="checkbox-icon"
              class="checkbox-input__icon-checked"
            />
          </button>
          <h1 class="subtitle-one">Tất cả</h1>
        </li>
        <li
          class="student-item d-flex c-p"
          v-for="subject in listSubject"
          :key="subject.id"
        >
          <button
            class="checkbox-input d-flex mg-r-8"
            :class="{ active: subject.selected }"
            @click="selectSubject(subject.id)"
          >
            <img
              src="../../assets/Icons/ic_Checkbox_Inactive.png"
              alt="checkbox-icon"
              class="checkbox-input__icon"
            />
            <img
              src="../../assets/Icons/ic_Checkbox_Hover.png"
              alt="checkbox-icon"
              class="checkbox-input__icon-hover"
            />
            <img
              src="../../assets/Icons/ic_Checkbox_Active.png"
              alt="checkbox-icon"
              class="checkbox-input__icon-checked"
            />
          </button>
          <h1 class="subtitle-one">{{ subject.name }}</h1>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// icon
import downIcon from "../../assets/Icons/ic_Chevron.png";
import deleteIcon from "../../assets/Icons/ic_X.png";

export default {
  name: "TagComp",
  props: {
    label: {
      type: String,
      default: "QL theo môn",
    },
    listSubject: {
      type: Array,
      default: () => [
        {
          id: "Math",
          name: "Toán",
          selected: true,
        },
        {
          id: "Physics",
          name: "Vật lý",
          selected: false,
        },
        {
          id: "Chemistry",
          name: "Hóa học",
          selected: true,
        },
        {
          id: "Bio",
          name: "Sinh học",
          selected: true,
        },
        {
          id: "History",
          name: "Lịch sử",
          selected: true,
        },
      ],
    },
  },
  data() {
    return {
      downIconUrl: downIcon,
      deleteIconUrl: deleteIcon,
      showListSubject: false,
      checkAll: false,
    };
  },
  methods: {
    /**
     * Show | un show các môn học
     * Author: Tran Danh (18/7/2022)
     */
    handleShowListSubject() {
      this.showListSubject = !this.showListSubject;
    },
    /**
     * Kích hoạt sự kiện -> check | uncheck môn học
     * Author: Tran Danh (18/7/2022)
     */
    selectSubject(idSubject) {
      this.$emit("selectSubject", idSubject);
      this.showCheckAll();
    },
    /**
     *  Xóa sự lựa chọn về môn học đó
     *  Author: Tran Danh (18/7/2022)
     */
    deleteSubject(idSubject) {
      this.$emit("deleteSubject", idSubject);
    },
    /**
     * Xử lý khi checkAll
     * Author: Tran Danh (18/7/2022)
     */
    handleCheckAll() {
      this.$emit("isCheckAll", this.checkAll);
      this.checkAll = !this.checkAll;
    },
    /**
     * Hiển checkAll khi check hết các subject và ngược lại
     * Author: Tran Danh (18/7/2022)
     */
    showCheckAll() {
      let numberSelected = 0;
      for (let i = 0; i < this.listSubject.length; i++) {
        if (this.listSubject[i].selected) {
          numberSelected += 1;
        }
      }

      this.checkAll = numberSelected === this.listSubject.length;
    },
    /**
     * Xử lý khi nhấn check all -> gửi 1 sự kiện lên
     * AUthor: Tran Danh (18/7/2022)
     */
    isCheckAll() {},
  },
  computed: {},
};
</script>

<style scoped>
.mg-r-8 {
  margin-right: 8px;
}

.tag-comp {
  position: relative;
  display: grid;
  grid-template-columns: var(--width-title-h-input) calc(
      100% - var(--width-title-h-input)
    );
  margin-bottom: 12px;
  min-width: 100%;
  height: var(--height-input);
}

.tag-comp .container {
  position: relative;
  margin-left: 12px;
  padding-top: 2px;
  padding-bottom: 2px;
}

.tag-comp__main {
  height: 100%;
  overflow-x: scroll;
  overflow-y: hidden;
}

.tag-comp__main::-webkit-scrollbar {
  width: 10px;
  cursor: pointer;
}
.tag-comp__main::-webkit-scrollbar:horizontal {
  height: 2px;
}
.tag-comp__main::-webkit-scrollbar-track {
  background-color: transparent;
}
.tag-comp__main::-webkit-scrollbar-thumb {
  border-radius: 10px;
  background: #fff;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}

.tag-comp .main__input {
  padding-left: 12px;
  width: 100%;
  height: 100%;
}

.tag-comp .main__input:focus {
  outline: unset;
}

.tag-comp__second {
  padding: 0 5px;
  height: 100%;
}

.tag-comp .list-student {
  position: absolute;
  top: calc(var(--height-input) + 8px);
  left: 0;
  right: 0;
  padding: 4px 0;
  margin-bottom: -1px;
  background: #fff;
  box-shadow: 0 0 5px #b1b1b1;
  justify-content: space-around;
  max-height: 180px;
  border-radius: 4px;
  overflow-y: scroll;
  display: none;
}

.tag-comp .list-student.show {
  display: block;
  z-index: 2;
}

.tag-comp .list-student::-webkit-scrollbar {
  width: 5px;
}

.tag-comp .list-student::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px #e5e5e5;
  border-radius: 4px;
}

.tag-comp .list-student::-webkit-scrollbar-thumb {
  background: #bbb;
  border-radius: 4px;
}

.tag-comp .list-title {
  height: 45px;
  padding: 0 12px;
  border-bottom: 1px solid #d5d5d5;
}

.tag-comp .student-item {
  padding-top: 8px;
  padding-left: 12px;
  padding-bottom: 8px;
}

.tag-comp .student-item:hover {
  background-color: var(--hover-color);
}

.tag__option {
  justify-content: space-between;
  background: #ccc;
  border-radius: 4px;
  height: 100%;
  margin: 2px 5px;
  padding-left: 10px;
  padding-right: 0;
}

.tag__option .content {
  color: #000;
  min-width: 60px;
}

.delete__option {
  height: 100%;
}

/* checkbox */
.checkbox-input {
  border: none;
  cursor: pointer;
  background-color: transparent;
}

.checkbox-input__icon-hover,
.checkbox-input__icon-checked {
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
</style>