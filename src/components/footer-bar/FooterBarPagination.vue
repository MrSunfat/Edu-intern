<template>
  <div class="footer__pagination d-flex">
    <div class="pagination__direction d-flex">
      <div class="first-page-icon d-flex c-p">
        <img src="../../assets/Icons/ic_MoveToFirst.png" alt="" />
      </div>
      <div class="prev-page-icon d-flex c-p" @click="handlePrevPage">
        <img src="../../assets/Icons/ic_Back.png" alt="" />
      </div>
      <input type="text" class="index-page" v-model="indexPage" />
      <div class="next-page-icon d-flex c-p" @click="handleNextPage">
        <img src="../../assets/Icons/ic_Next.png" alt="" />
      </div>
      <div class="last-page-icon d-flex c-p">
        <img src="../../assets/Icons/ic_MoveToLast.png" alt="" />
      </div>
      <div class="number-page-current subtitle-two fs-t-14 d-flex c-p">
        1/10 trang (
        <h1 class="subtitle-one fs-t-14 result">496</h1>
        &nbsp; kết quả)
      </div>
    </div>
    <div class="pagination__btns">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  name: "FooterBarPagination",
  data() {
    return {
      indexPage: 1,
    };
  },
  methods: {
    handlePrevPage() {
      if (this.indexPage > 1) {
        this.indexPage = parseInt(this.indexPage) - 1;
      }
    },
    handleNextPage() {
      this.indexPage = parseInt(this.indexPage) + 1;
      // if (this.indexPage > 2) {
      // }
    },
  },
  computed: {},
};
</script>

<style scoped>
.footer__pagination {
  position: absolute;
  justify-content: space-between;
  left: 0;
  right: 0;
  bottom: 0;
  padding-top: 12px;
  padding-bottom: 12px;
  height: var(--height-pagination);
  /* background-color: aqua; */
  box-shadow: 0 0 5px #b1b1b1;
  background-color: #fff;
}

.pagination__direction {
  justify-content: space-between;
  padding-left: 16px;
}

.first-page-icon {
  margin-right: 4px;
}

.index-page {
  text-align: center;
  width: 64px;
  height: 32px;
  border-radius: 4px;
  border: 1px solid var(--second-btn-bd);
  color: var(--input-text-color);
  margin: 0 10px;
}

.index-page:focus {
  outline: unset;
}

.next-page-icon {
  margin-right: 3px;
}

.last-page-icon {
  margin-right: 10px;
}

.number-page-current > .result {
  line-height: 19px;
}

.pagination__btns .btn__save {
  margin-left: 8px;
  margin-right: 16px;
}

.pagination__btns {
  padding-right: 16px;
}
</style>