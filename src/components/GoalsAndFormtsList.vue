<template>
  <div class="goals-and-formats-list">
    <draggable
      v-model="list"
      group="goals-and-formats"
      ghost-class="goals-and-formats-list__dragging"
      @start="drag = true"
      @end="drag = false"
      item-key="id"
    >
      <template #item="{ element }">
        <GoalsAndFormatsItem
          v-model:is-active="element.isActive"
          v-model:control="element.control"
          :data="element"
        >
        </GoalsAndFormatsItem>
      </template>
    </draggable>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
import GoalsAndFormatsItem from '@/components/GoalsAndFormatsItem';

export default {
  components: {
    GoalsAndFormatsItem,
    draggable,
  },
  data() {
    return {
      drag: false,
      list: [
        { isActive: true, title: 'Educate', text: 'Publication frequency:', control: 4, id: 0 },
        { isActive: false, title: 'Inform', text: 'Publication frequency:', control: 4, id: 1 },
        { isActive: true, title: 'Inform', text: 'Publication frequency:', control: 4, id: 2 },
        { isActive: false, title: 'Educate', text: 'Publication frequency:', control: 4, id: 3 },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
.goals-and-formats-list {
  padding: 20px;
  background: #fafafa;

  &__dragging {
    opacity: 0.5;
    background: #c8ebfb;
  }
}
</style>
