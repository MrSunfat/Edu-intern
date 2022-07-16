<template>
  <div class="table-teachers">
    <table class="table-teachers__container">
      <tr class="table-teachers__container__title">
        <th class="title">
          <button
            class="checkbox-input d-flex"
            :class="this.checkAll && 'active'"
            v-on:click="handleToggleCheckedAll"
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
        </th>
        <th
          class="title center-text"
          v-for="info in this.infoTeacher"
          :key="info"
        >
          {{ info }}
        </th>
      </tr>
      <row-table-teachers
        v-for="teacher in this.fakeDbTeacher"
        :key="teacher.code"
        :teacher="teacher"
        v-on:toggelChecked="handleToggleChecked"
      />
    </table>
  </div>
</template>

<script>
import RowTableTeachers from "../common/row-table/RowTableTeachers.vue";
export default {
  components: { RowTableTeachers },
  name: "TableTeachers",
  data() {
    return {
      /* 
            Các thông tin của 1 cán bộ, giáo viên
            -> tiêu đề cho các cột
        */
      infoTeacher: [
        "Số hiệu cán bộ",
        "Họ và tên",
        "Số điện thoại",
        "Tổ chuyên môn",
        "QL theo môn",
        "QL kho, phòng",
        "Đào tạo QLTB",
        "Đang làm việc",
        "",
      ],
      fakeDbTeacher: [
        {
          code: "MS15001",
          fullName: "Nguyễn Lê Lan Anh",
          phone: "0360368999",
          group: "Tổ Toán - Tin",
          subject: "Toán",
          lab: "Phòng Hóa - Sinh",
          training: true,
          jobStatus: true,
        },
        {
          code: "MS15002",
          fullName: "Nguyễn Lê Thiết",
          phone: "012346",
          group: "Tổ Hóa",
          subject: "Hóa Sinh",
          lab: "Phòng Toán",
          training: false,
          jobStatus: true,
        },
        {
          code: "MS15003",
          fullName: "Nguyễn Lê Thiết",
          phone: "012346",
          group: "Tổ Hóa",
          subject: "Hóa Sinh",
          lab: "Phòng Toán",
          training: false,
          jobStatus: true,
        },
        {
          code: "MS15004",
          fullName: "Nguyễn Lê Thiết",
          phone: "012346",
          group: "Tổ Hóa",
          subject: "Hóa Sinh",
          lab: "Phòng Toán",
          training: false,
          jobStatus: true,
        },
        {
          code: "MS15005",
          fullName: "Nguyễn Lê Thiết",
          phone: "012346",
          group: "Tổ Hóa",
          subject: "Hóa Sinh",
          lab: "Phòng Toán",
          training: false,
          jobStatus: true,
        },
      ],
      checkAll: false,
    };
  },
  methods: {
    /*
      Xử lý khi nhấn nút check hoặc bỏ check toàn bộ
    */
    handleToggleCheckedAll() {
      this.checkAll = !this.checkAll;
      if (this.checkAll) {
        this.fakeDbTeacher = this.fakeDbTeacher.map((db) => {
          // console.log(db);
          return { ...db, checked: true };
        });
      } else {
        this.fakeDbTeacher = this.fakeDbTeacher.map((db) => {
          // console.log(db);
          return { ...db, checked: false };
        });
      }

      // console.log(fakeDbTeacher);
    },
    /*
      Xử lý sự kiện check của từng hàng trong bảng
    */
    handleToggleChecked(data) {
      // console.log(data);
      const posRow = this.fakeDbTeacher.findIndex((row) => row.code === data);
      this.fakeDbTeacher[posRow].checked = !this.fakeDbTeacher[posRow].checked;
      // console.log(this.fakeDbTeacher);
      this.handleUnCheckedRow();
    },
    /*
      - Xử lý khi các hàng check hết -> nút checkAll được check
      - Xử lý khi các hàng không check -> nút checkAll phải uncheck
    */
    handleUnCheckedRow() {
      const lengthDb = this.fakeDbTeacher.length;
      // lưu số hàng đã check
      let lengthRowChecked = 0;
      this.fakeDbTeacher.forEach((db) => {
        if (db.checked) {
          lengthRowChecked += 1;
        }
      });

      // Xét số hàng đã check vs số hàng trong bảng
      if (lengthRowChecked === lengthDb) {
        this.checkAll = true;
      } else {
        this.checkAll = false;
      }

      // console.log(lengthRowChecked);
    },
  },
  computed: {},
  created() {
    this.fakeDbTeacher = this.fakeDbTeacher.map((db) => {
      // console.log(db);
      return { ...db, checked: false };
    });
  },
};
</script>

<style scoped>
@import url("../../style/components/table/table-teachers.css");
</style>