<template>
  <div class="content">
    <!-- content -->
    <system-page />
  </div>
</template>

<script>
// import FooterBarPagination from '../footer-bar/FooterBarPagination.vue';
import SystemPage from "../pages/SystemPage.vue";
export default {
  name: "TheContent",
  data() {
    return {
      closeFormAdd: false,
    };
  },
  components: {
    SystemPage,
  },
  methods: {
    handleCloseFormAddTeacher(data) {
      this.closeFormAdd = data;
    },
  },
};
</script>

<style scoped>
.content {
  position: relative;
  overflow: hidden;
  padding: 0 16px;
}
</style>