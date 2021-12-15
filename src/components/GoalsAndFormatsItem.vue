<template>
  <a-card class="goals-and-format-item" :class="{ disabled: !isActive }" hoverable>
    <template #title>
      <a-switch :checked="isActive" @update:checked="$emit('update:is-active', $event)"></a-switch>

      {{ data.title }}
    </template>

    <template #extra>
      <drag-outlined />
    </template>

    <div class="goals-and-format-item__content">
      <p>{{ data.text }}</p>
      <a-input
        :value="control"
        :disabled="!isActive"
        @update:checked="$emit('update:control', $event)"
      ></a-input>
      <slot></slot>
    </div>
  </a-card>
</template>

<script>
import { DragOutlined } from '@ant-design/icons-vue';

export default {
  name: 'GoalsAndFormatsItem',
  props: ['data', 'isActive', 'control'],
  components: [DragOutlined],
};
</script>

<style scoped lang="scss">
.goals-and-format-item {
  & + & {
    margin-top: 15px;
  }

  &.disabled {
    background-color: #fafafa;
    color: #bfbfbf;
  }
}
</style>
