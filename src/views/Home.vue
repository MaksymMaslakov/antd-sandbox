<template>
  <Header />
  <a-tabs type="card" v-model:activeKey="activeTab">
    <a-tab-pane key="1" tab="General" class="tab-content">
      <PublicationDaysList />
    </a-tab-pane>
    <a-tab-pane key="2" tab="Calendar" class="tab-content">
      <TestCalendar />
    </a-tab-pane>
  </a-tabs>
</template>

<script>
import Header from "@/components/Header.vue";
import PublicationDaysList from "@/components/PublicationDaysList.vue";
import TestCalendar from "@/components/TestCalendar.vue";

export default {
  name: "Home",
  components: {
    Header,
    PublicationDaysList,
    TestCalendar,
  },
  data() {
    return {
      activeTab: 2,
    };
  },
};
</script>

<style scoped lang="scss">
.tab-content {
  background: #e5e5e5;
  padding: 20px 25px;
}
</style>
