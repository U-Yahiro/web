<template>
  <component
    :is="icon.element ? icon.element : 'i'"
    class="vsm--icon"
    :class="
      typeof icon === 'string' || icon instanceof String ? icon : icon.class
    "
    v-bind="icon.attributes"
  >
    {{ icon.text }}
  </component>
</template>

<script>
export default {
  name: "SidebarMenuIcon",
  props: {
    icon: {
      type: [String, Object],
      default: ""
    }
  }
};
</script>
<style scoped>
.v-sidebar-menu .vsm--link_level-1 .vsm--icon {
    background-color: #0f273e;
}
</style>
