<template>
  <div class="popup-form-add-teacher">
    <div class="form-add-teacher">
      <div class="form-add-teacher__avatar-container">
        <div class="avatar-box__img d-flex">
          <div class="avatar-box-img">
            <img
              src="../../assets/Icons/ic_Avatar_36.png"
              alt=""
              class="avatar-img"
            />
          </div>
          <h1
            class="subtitle-two center-text avatar-box__subtitle"
            @click="handleFileInputAvatar"
          >
            Chọn ảnh
          </h1>
          <input ref="filInputAvatar" type="file" class="file-input-avatar" />
        </div>
        <div class="avatar-box__info d-flex">
          <h1 class="title">Họ và tên</h1>
          <p class="subtitle-two">Số hiệu cán bộ</p>
        </div>
      </div>
      <div class="form-add-teacher__inputs">
        <h1 class="title">Thêm hồ sơ Cán bộ, giáo viên</h1>
        <div class="inputs__main mg-t-16">
          <div class="inputs__main__one">
            <h-label-input
              label="Số hiệu cán bộ"
              :binding="true"
              :tabindex="1"
              stringRef="firstFocus"
              :class="{
                error: this.validateBinding.code.length > 0 ? true : false,
              }"
            />
            <h-label-input
              label="Họ và tên"
              :binding="true"
              :tabindex="2"
              stringRef="twoFocus"
              :class="{
                error: this.validateBinding.fullName.length > 0 ? true : false,
              }"
            />
            <h-label-input label="Số điện thoại" :tabindex="3" />
            <h-label-input label="Email" :tabindex="4" />
            <drop-down-one
              label="Tổ hợp môn"
              :binding="false"
              :dbDropdown="dbDropdown"
              v-on:changeOption="handleChangeOption"
            />
            <tag-comp
              :listSubject="listSubject"
              @selectSubject="handleSelectSubject"
              @isCheckAll="isCheckAll"
              @deleteSubject="deleteSubject"
            />
          </div>
          <div class="inputs__main__two">
            <!-- <drop-down-one /> -->
          </div>
          <!-- <drop-down-one /> -->
          <div class="inputs__main__three d-flex">
            <div class="career-level d-flex">
              <button
                class="checkbox-input d-flex none-pd-l mg-r-8"
                :class="this.careerLevel && 'active'"
                v-on:click="handleToggleCareerLevel"
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
              <h1 class="subtitle-two">Trình độ nghiệp vụ QLTB</h1>
            </div>
            <div class="working d-flex mg-l-8">
              <button
                class="checkbox-input d-flex mg-r-8"
                :class="this.working && 'active'"
                v-on:click="handleToggleWorking"
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
              <h1 class="subtitle-two">Đang làm việc</h1>
            </div>
            <input-date v-show="showDayOff" />
          </div>
          <tag-comp
            :listSubject="listGroup"
            @selectSubject="handleSelectSubject"
            @isCheckAll="isCheckAll"
            @deleteSubject="deleteSubject"
            typeTag="lab"
          />
        </div>
        <div class="inputs__btns mg-t-16">
          <base-btn
            class="inputs__btns__close"
            type="second-btn"
            nameBtn="Đóng"
            :handleClick="handleCloseFormAddTeacher"
          />
          <base-btn
            class="inputs__btns__save mg-l-8"
            type="primary-btn"
            nameBtn="Lưu"
            :handleClick="validateForm"
          />
          <!-- v-on:selectOption="handleSelectOption" -->
        </div>
      </div>
      <div class="form-add-teacher__close" @click="handleCloseFormAddTeacher">
        <img src="../../assets/Icons/ic_X_2.png" alt="" class="close-icon" />
      </div>
    </div>
    <!-- <toast-fail :class="{ show: this.showToast.toastFail }" /> -->
  </div>
</template>

<script>
import BaseBtn from "../common/button/BaseBtn.vue";
import DropDownOne from "../input/DropDownOne.vue";
import HLabelInput from "../input/horizontal/HLabelInput.vue";
import InputDate from "../input/InputDate.vue";
import TagComp from "../input/TagComp.vue";
export default {
  components: {
    HLabelInput,
    DropDownOne,
    InputDate,
    BaseBtn,
    TagComp,
  },
  name: "FormAddTeacher",
  data() {
    return {
      careerLevel: false,
      working: false,
      showDayOff: true,
      dbDropdown: {
        listSubjectGroup: [
          {
            name: "Tổ toán tin",
            selected: false,
          },
          {
            name: "Tổ hóa lý",
            selected: true,
          },
          {
            name: "Tổ sinh",
            selected: false,
          },
          {
            name: "Tổ sử địa",
            selected: false,
          },
          {
            name: "Tổ văn học",
            selected: false,
          },
        ],
        optionSelected: "",
      },
      validateBinding: {
        code: "",
        fullName: "",
      },
      showToast: {
        toastSuccess: false,
        toastFail: false,
      },
      listSubject: [
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
      listGroup: [
        {
          id: "math-lab",
          name: "Phòng Toán-Lý",
          selected: false,
        },
        {
          id: "chemistry-lab",
          name: "Phòng Hóa-Sinh",
          selected: true,
        },
        {
          id: "common-room",
          name: "Kho phòng chung",
          selected: true,
        },
      ],
    };
  },
  methods: {
    /*
      Checkbox Trình độ nghiệp vụ QLTB
      Author: Tran Danh (16/7/2022)
    */
    handleToggleCareerLevel() {
      this.careerLevel = !this.careerLevel;
    },
    /*
      Checkbox đang làm việc
      Author: Tran Danh (16/7/2022)
    */
    handleToggleWorking() {
      this.showDayOff = !this.showDayOff;
      this.working = !this.working;
    },
    /*
      Đóng form thêm cán bộ
      Author: Tran Danh (16/7/2022)
    */
    handleCloseFormAddTeacher() {
      this.$emit("closeFormAddTeacher", true);
    },
    /*
      Xử lý khi lưu dữ liệu
      Author: Tran Danh (16/7/2022)
    */
    validateForm() {
      this.validateBinding.code = this.$refs.firstFocus.value;
      this.validateBinding.fullName = this.$refs.twoFocus.value;

      console.log(this.validateBinding);

      // if (
      //   this.validateBinding.code.length > 0 &&
      //   this.validateBinding.fullName.length > 0
      // ) {
      //   this.showToast.toastSuccess = true;
      //   this.showToast.toastFail = false;
      // } else {
      //   this.showToast.toastSuccess = false;
      //   this.showToast.toastFail = true;
      // }
    },
    /*
      Xử lý khi chọn option khác trong dropdown
      Author: Tran Danh (16/7/2022)
    */
    handleChangeOption(nameOption) {
      for (let i = 0; i < this.dbDropdown.listSubjectGroup.length; i++) {
        if (this.dbDropdown.listSubjectGroup[i].name === nameOption) {
          this.dbDropdown.listSubjectGroup[i].selected = true;
        } else {
          this.dbDropdown.listSubjectGroup[i].selected = false;
        }
      }
      this.findOptionSelected();
    },
    /**
     * Tìm tên option được chọn trong 1 list các option
     * Author: Tran Danh (16/7/2022)
     */
    findOptionSelected() {
      for (let i = 0; i < this.dbDropdown.listSubjectGroup.length; i++) {
        if (this.dbDropdown.listSubjectGroup[i].selected) {
          this.dbDropdown.optionSelected =
            this.dbDropdown.listSubjectGroup[i].name;
        }
      }
    },
    /**
     * Chọn avatar
     * Author: TRan Danh (16/7/2022)
     */
    handleFileInputAvatar() {
      this.$refs.filInputAvatar.click();
    },
    /**
     * Tag Component
     */
    /**
     * Xử lý khi chọn subject
     */
    handleSelectSubject(idOption) {
      const idxOption = this.listSubject.findIndex(
        (subject) => subject.id === idOption
      );

      this.listSubject[idxOption].selected =
        !this.listSubject[idxOption].selected;
    },
    /**
     * Xử lý khi nhấn check all
     * Author: Tran Danh (18/7/2022)
     */
    isCheckAll(checkAll) {
      if (!checkAll) {
        for (let i = 0; i < this.listSubject.length; i++) {
          this.listSubject[i].selected = true;
        }
      } else {
        for (let i = 0; i < this.listSubject.length; i++) {
          this.listSubject[i].selected = false;
        }
      }
    },
    /**
     * Nhận sự kiện từ TagComp
     * -> xét selected của subject đó = false
     * AUthor: Tran Danh (18/7/2022)
     */
    deleteSubject(idSubject) {
      for (let i = 0; i < this.listSubject.length; i++) {
        if (this.listSubject[i].id === idSubject) {
          this.listSubject[i].selected = false;
        }
      }
    },
  },
  beforeMount() {
    this.findOptionSelected();
  },
  computed: {},
};
</script>

<style scoped>
.popup-form-add-teacher {
  position: fixed;
  content: "";
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.85);
  display: none;
}

.popup-form-add-teacher.show {
  display: flex;
  align-items: center;
}

.form-add-teacher {
  position: relative;
  display: grid;
  grid-template-columns: 25% 75%;
  padding-top: 8px;
  padding-bottom: 16px;
  width: 800px;
  background-color: #fff;
  margin: 20px auto;
  border-radius: 4px;
}

/* avatar */
.form-add-teacher__avatar-container {
  border-right: 1px solid var(--line-gridpanel-color);
  padding-top: 8px;
}

.avatar-box__img {
  flex-direction: column;
  padding: 0 24px;
}

.avatar-box-img {
  background-color: var(--bg-color);
  height: 150px;
  width: 100%;
}

.avatar-box__subtitle {
  background-color: var(--main-color);
  width: 100%;
  color: #fff;
  border-bottom-left-radius: 4px;
  border-bottom-right-radius: 4px;
  padding-top: 8px;
  padding-bottom: 8px;
  cursor: pointer;
}

.avatar-img {
  background: url("../../assets/Icons/ic_Avatar_36.png") no-repeat -488px -67px;
  width: 100%;
  height: 100%;
}

.avatar-box__info {
  flex-direction: column;
  justify-content: center;
  margin-top: 20px;
}

.avatar-box__info p.subtitle-two {
  margin: 0;
  font-size: 12px;
}

/* inputs */
.form-add-teacher__inputs {
  padding-top: 8px;
  padding-left: 24px;
  padding-right: 24px;
  color: var(--second-color-in-form);
}

.form-add-teacher__inputs > h1.title {
  color: var(--main-color-in-form);
  font-size: 20px;
}

.inputs__main {
  width: 100%;
}

.inputs__main__one,
.inputs__main__two {
  display: grid;
  grid-template-columns: 6fr 6fr;
  grid-column-gap: 16px;
  min-width: 100%;
  max-width: min-content;
}

.inputs__main__three {
  width: 100%;
}

/* btn */
.inputs__btns {
  text-align: right;
}

.inputs__btns__save {
}

.form-add-teacher__close {
  position: absolute;
  content: "";
  top: 6px;
  right: 6px;
  cursor: pointer;
}

.file-input-avatar {
  display: none;
}
</style>