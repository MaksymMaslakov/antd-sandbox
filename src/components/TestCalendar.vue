<template>
  <a-row class="calendar">
    <a-col span="16">
      <a-calendar v-model:value="value" @select="handlerSelect($event, value)">
        <template #dateCellRender="{ current }">
          <div class="media-list">
            <div
              v-for="item in getListData(current)"
              :key="item.content"
              class="media-list__item"
            >
              <base-media-icon :icon-type="item.type" />
            </div>
          </div>
        </template>
      </a-calendar>
    </a-col>

    <a-col span="8">
      <div class="calendar__aside calendar-notes">
        <h3 class="calendar-notes__month">Month</h3>
        <p class="calendar-notes__description">Group title</p>
        <div class="calendar-notes__media-list">
          <media-note
            v-for="(item, index) in items"
            :key="index"
            :data="item"
          />
        </div>
      </div>
    </a-col>
  </a-row>
</template>

<script>
import { defineComponent, ref } from "vue";
import BaseMediaIcon from "@/components/base-components/BaseMediaIcon";
import MediaNote from "@/components/MediaNote";

export default defineComponent({
  components: { MediaNote, BaseMediaIcon },
  setup() {
    const value = ref();
    let items = ref();

    const getListData = (value) => {
      let listData;
      switch (value.date()) {
        case 8:
          listData = [
            {
              type: "twitter",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "instagram",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "facebook",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
          ];
          break;
        case 10:
          listData = [
            {
              type: "instagram",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "facebook",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "twitter",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
          ];
          break;
        case 15:
          listData = [
            {
              type: "facebook",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "twitter",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "instagram",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "facebook",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "twitter",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "instagram",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "twitter",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "instagram",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
            {
              type: "facebook",
              title: "Image",
              description: "Description",
              text: "This is warning event.",
              time: "15:43",
            },
          ];
          break;
        default:
      }
      return listData || [];
    };

    const handlerSelect = (date) => {
      items.value = getListData(date);
    };

    return {
      value,
      items,
      getListData,
      handlerSelect,
    };
  },
});
</script>
<style scoped lang="scss">
.calendar-notes {
  background: #ffffff;
  height: 100%;
  padding: 15px;
}

.media-list {
  $size: 24px;

  height: $size;
  display: flex;
  flex-wrap: wrap;
  padding-right: 15px;

  &__item {
    width: 15px;
  }

  &__media-list {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }
}
.notes-month {
  text-align: center;
  font-size: 28px;
}
.notes-month section {
  font-size: 28px;
}
</style>
