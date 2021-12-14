<template>
  <a-button shape="circle" class="social-network">
    <template #icon>
      <component :is="getIconComponent(iconType)" />
    </template>
  </a-button>
</template>

<script>
import {
  TwitterOutlined,
  InstagramOutlined,
  FacebookOutlined,
} from "@ant-design/icons-vue";
import { FACEBOOK, INSTAGRAM, TWITTER } from "@/constants/social-types";

export default {
  name: "BaseMediaIcon",
  components: { TwitterOutlined, InstagramOutlined, FacebookOutlined },
  props: {
    iconType: {
      type: String,
    },
  },
  methods: {
    getIconComponent(iconType) {
      let iconComponent;

      switch (iconType) {
        case TWITTER:
          iconComponent = "twitter-outlined";
          break;
        case INSTAGRAM:
          iconComponent = "instagram-outlined";
          break;
        case FACEBOOK:
          iconComponent = "facebook-outlined";
          break;
        default:
          iconComponent = "info-circle-outlined";
      }

      return iconComponent;
    },
  },
};
</script>

<style scoped lang="scss">
.social-network {
  display: inline-block;
}
</style>
