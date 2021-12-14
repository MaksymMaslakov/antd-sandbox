<template>
  <a-card class="publication-days" title="Publication days" :bordered="false">
    <PublicationDay
      v-for="item in daysDataList"
      :key="item.label"
      :label="item.label"
      v-model:is-active="item.isActive"
      v-model:time-ranges="item.timeRanges"
    />
  </a-card>
</template>

<script>
import PublicationDay from "@/components/PublicationDay";

export default {
  name: "PublicationDaysList",
  components: {
    PublicationDay,
  },
  data() {
    return {
      daysDataList: [
        {
          label: "Monday",
          isActive: false,
          timeRanges: [{ from: "00:00", to: "00:00" }],
        },
        {
          label: "Tuesday",
          isActive: true,
          timeRanges: [{ from: "00:00", to: "00:00" }],
        },
        {
          label: "Wednesday",
          isActive: true,
          timeRanges: [{ from: "00:00", to: "00:00" }],
        },
        {
          label: "Thursday",
          isActive: true,
          timeRanges: [{ from: "00:00", to: "00:00" }],
        },
        {
          label: "Friday",
          isActive: false,
          timeRanges: [{ from: "00:00", to: "00:00" }],
        },
        {
          label: "Saturday",
          isActive: true,
          timeRanges: [{ from: "00:00", to: "00:00" }],
        },
        {
          label: "Sunday",
          isActive: false,
          timeRanges: [{ from: "00:00", to: "00:00" }],
        },
      ],
    };
  },
  watch: {
    daysDataList: {
      deep: true,
      handler(value) {
        console.log(value);
      },
    },
  },
};
</script>

<style scoped lang="scss"></style>
