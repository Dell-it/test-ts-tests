<template>
  <svg :class="className" xmlns="http://www.w3.org/2000/svg">
    <title v-if="title">{{ title }}</title>
    <use :xlink:href="iconPath" xmlns:xlink="http://www.w3.org/1999/xlink" />
  </svg>
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  name: "svg-icon",

  props: {
    name: {
      type: String,
      required: true,
    },

    title: {
      type: String,
      default: null,
    },
  },

  computed: {
    iconPath() {
      // eslint-disable-next-line @typescript-eslint/no-var-requires
      let icon = require(`@/assets/svg/${this.name}.svg`);
      if (Object.prototype.hasOwnProperty.call(icon, "default")) {
        icon = icon.default;
      }
      return icon.url;
    },

    className() {
      return "svg-icon svg-icon--" + this.name;
    },
  },
});
</script>

<style>
.svg-icon {
  fill: currentColor;
}
</style>
