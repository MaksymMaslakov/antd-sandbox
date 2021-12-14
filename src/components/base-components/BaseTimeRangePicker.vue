<template>
  <div class="time-range">
    <a-time-picker
      ref="firstTimeRange"
      :value="timeRange.from"
      :format="timeFormat"
      :valueFormat="timeFormat"
      :disabledHours="disabledHours"
      :disabledMinutes="disabledMinutes"
      @change="onChangeFirstTimePicker"
    />

    <span>-</span>

    <a-time-picker
      ref="secondTimeRange"
      :value="timeRange.to"
      :format="timeFormat"
      :valueFormat="timeFormat"
      :disabledHours="disabledHours"
      :disabledMinutes="disabledMinutes"
      @change="onChangeSecondTimePicker"
    />
    <a-button v-show="!isSingleRange" type="link">
      <template #icon>
        <CloseSquareFilled @click="$emit('remove', timeRange)" />
      </template>
    </a-button>
  </div>
</template>

<script>
/* eslint-disable */
import { CloseSquareFilled } from "@ant-design/icons-vue";

export default {
  name: "BaseTimeRangePicker",
  components: {
    CloseSquareFilled,
  },
  emits: ["update:time-range", "remove"],
  props: {
    timeRange: {
      required: true,
      type: Object,
    },
    timeFormat: {
      required: true,
      type: String,
    },
    disabledTime: {
      default: "00:00",
    },
    index: Number,
    length: Number,
  },
  computed: {
    isSingleRange() {
      return this.length === 1;
    },
    isReplaceFromWithTo() {
      return (
        this.fromHours > this.toHours ||
        (this.fromHours === this.toHours && this.fromMinutes > this.toMinutes)
      );
    },
    fromHours() {
      return +this.timeRange.from?.split(":")[0];
    },
    toHours() {
      return +this.timeRange.to?.split(":")[0];
    },
    fromMinutes() {
      return +this.timeRange.from?.split(":")[1];
    },
    toMinutes() {
      return +this.timeRange.to?.split(":")[1];
    },
  },
  methods: {
    onChangeFirstTimePicker(value) {
      this.timeRange.from = value;

      if (this.isReplaceFromWithTo) {
        this.timeRange.to = this.timeRange.from;
      }

      this.$emit("update:time-range", this.timeRange, this.index);
      this.$refs.secondTimeRange.focus();
    },
    onChangeSecondTimePicker(value) {
      this.timeRange.to = value;

      if (this.isReplaceFromWithTo) {
        const temp = this.timeRange.from;
        this.timeRange.from = this.timeRange.to;
        this.timeRange.to = temp;
      }

      this.$emit("update:time-range", this.timeRange, this.index);
    },
    disabledHours() {
      const hours = [];

      for (let i = 0; i < +this.disabledTime?.split(":")[0]; i++) {
        hours.push(i);
      }

      return hours;
    },
    disabledMinutes(selectedHours) {
      const minutes = [];

      if (selectedHours <= +this.disabledTime?.split(":")[0]) {
        for (let i = 0; i < +this.disabledTime?.split(":")[1]; i++) {
          minutes.push(i);
        }
      }

      return minutes;
    },
  },
};
</script>

<style scoped lang="scss">
.time-range {
  display: flex;
  align-items: center;
  gap: 15px;

  &:not(:first-of-type)::before {
    content: "and";
    font-style: italic;
  }
}
</style>
