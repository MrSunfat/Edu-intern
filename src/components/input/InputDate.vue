<template>
  <div class="input-date d-flex">
    <label for="day-off" class="subtitle-two d-flex">Ngày nghỉ việc</label>
    <div class="input-date__main d-flex">
      <input id="day-off" class="main__box" type="date" :value="this.dataDateDefault" />
    </div>
  </div>
</template>

<script>
export default {
  name: "InputDate",
  data() {
    return {
      dataDateDefault: new Date("2020-06-22").toISOString().slice(0,10)
    }
  }
};
</script>

<style scoped>
.input-date {
  height: var(--height-input);
}

.input-date__main {
  margin-left: 12px;
}

.input-date__main .main__box {
  height: 32px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 0;
  padding-left: 12px;
  cursor: pointer;
}

.input-date__main .main__box:focus {
    outline: unset;
}

.input-date__main .main__box::-webkit-datetime-edit-text {
  color: #555555;
  /* margin-left: 12px; */
}

.input-date__main .main__box::-webkit-calendar-picker-indicator {
  background: url('../../assets/Icons/ic_sprites.svg') no-repeat -904px -112px;
  color: rgba(204, 204, 204, 0);
  border-left: 1px solid #ccc;
  padding: 0 12px;
  height: 100%;
  cursor: pointer;
}
</style>