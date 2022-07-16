<template>
  <div class="tag-comp i-d-flex">
    <div class="label">{{ label }}</div>
  </div>
</template>

<script>
export default {
  name: "TagComp",
  props: {
    label: {
      type: String,
      default: "QL theo môn",
    },
  },
};
</script>

<style>
</style>