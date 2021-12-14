<template>
  <div class="publication-day">
    <a-switch
      :checked="isActive"
      @update:checked="this.$emit('update:is-active', $event)"
    ></a-switch>

    <span>{{ label }}</span>

    <template v-if="isActive">
      <base-time-range-picker
        v-for="(timeRange, index) in timeRanges"
        :key="index"
        :time-range="timeRange"
        :time-format="timeFormat"
        :length="timeRanges.length"
        :index="index"
        :disabled-time="disabledTime"
        @update:time-range="onUpdateRange"
        @remove="onRemoveRange"
      >
      </base-time-range-picker>

      <a-button v-show="isAddButtonShow" type="link" @click="onAddRange">
        + add a period
      </a-button>
    </template>

    <template v-else> No publication </template>
  </div>
</template>

<script>
import BaseTimeRangePicker from "@/components/base-components/BaseTimeRangePicker";

export default {
  name: "PublicationDay",
  components: { BaseTimeRangePicker },
  props: ["label", "isActive", "timeRanges"],
  data() {
    return {
      maxItemsInRow: 3,
      timeFormat: "HH:mm",
      disabledTime: "00:00",
    };
  },
  computed: {
    isAddButtonShow() {
      return this.timeRanges.length < this.maxItemsInRow;
    },
  },
  methods: {
    onAddRange() {
      const previousItem = this.timeRanges[this.timeRanges.length - 1];
      const newItem = {
        from: previousItem.to,
        to: previousItem.to,
      };
      this.disabledTime = previousItem.to;
      const newTimeRanges = [...this.timeRanges];
      newTimeRanges.push(newItem);

      this.$emit("update:time-ranges", newTimeRanges);
    },
    onUpdateRange(changedItem, index) {
      const newTimeRanges = [...this.timeRanges];
      newTimeRanges.splice(index, 1, changedItem);

      this.$emit("update:time-ranges", newTimeRanges);
    },
    onRemoveRange(removedItem) {
      const newTimeRanges = this.timeRanges.filter((item) => {
        return !Object.is(item, removedItem);
      });
      this.$emit("update:time-ranges", newTimeRanges);
    },
    onUpdateIsActive(value) {
      this.$emit("update:is-active", value);
    },
  },
};
</script>

<style scoped lang="scss">
.publication-day {
  display: grid;
  grid-template-columns: 40px 120px 240px 280px 280px;
  align-items: center;
  gap: 15px;
  height: 32px;

  &__time-range {
    display: flex;
    align-items: center;
    gap: 15px;
  }

  & + & {
    margin-top: 15px;
  }
}
</style>
