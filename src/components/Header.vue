<template>
  <header class="page-header">
    <a-space>
      <!--@todo: reduce inline style-->
      <a-typography-title class="page-header__title">
        Edit distribution of user id 2432
      </a-typography-title>

      <a-tag color="green">active</a-tag>
    </a-space>

    <a-space>
      <a-button size="large">Cancel</a-button>
      <a-button size="large">Reset original</a-button>
      <!--@todo: set success button-->
      <!--@todo: add icon-->
      <a-button size="large">
        Save and Close
        <template #icon>
          <SaveOutlined />
        </template>
      </a-button>
    </a-space>
  </header>
</template>

<script>
import { SaveOutlined } from "@ant-design/icons-vue";

export default {
  name: "Header",
  components: {
    SaveOutlined,
  },
};
</script>

<style scoped lang="scss">
.page-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 25px;

  &__title {
    margin: 0 !important;
  }
}
</style>
