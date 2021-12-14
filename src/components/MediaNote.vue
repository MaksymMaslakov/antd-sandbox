<template>
  <a-card>
    <template #title>
      <base-media-icon :icon-type="data.type" />

      {{ data.title }}
    </template>

    <template #extra>{{ data.time }}</template>

    {{ data.text }}
    <slot></slot>
  </a-card>
</template>

<script>
import BaseMediaIcon from "@/components/base-components/BaseMediaIcon";
export default {
  name: "MediaNote",
  components: { BaseMediaIcon },
  props: ["data"],
};
</script>

<style scoped></style>
