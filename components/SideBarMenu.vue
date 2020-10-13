<template>
  <div class="container">
    <sidebar-menu :menu="menu" />
    <sidebar-menu
      @toggle-collapse="onToggleCollapse"
      @item-click="onItemClick"
    />
  </div>
</template>

<script>
const separator = {
  template: `<hr style="border-color: rgba(0, 0, 0, 0.3); margin: 20px;">`
};

export default {
  name: "App",
  data() {
    return {
      props: {
        // Sidebar menu (required)
        menu: {
          type: Array,
          required: true
        },

        // Sidebar Collapse state
        collapsed: {
          type: Boolean,
          default: false
        },

        // Sidebar width,(expanded)
        Sidebarwidth: {
          type: String,
          default: "300px"
        },

        // Sidebar width (collapsed)
        widthCollapsed: {
          type: String,
          default: "50px"
        },

        // Keep only one child opened at a time (first level only)
        showOneChild: {
          type: Boolean,
          default: false
        },

        // Keep all child open
        showChild: {
          type: Boolean,
          default: false
        },

        // Sidebar right to left
        rtl: {
          type: Boolean,
          default: false
        },

        // Make sidebar relative to the parent (by default the sidebar is relative to the viewport)
        relative: {
          type: Boolean,
          default: false
        },

        // Hide toggle collapse btn
        hideToggle: {
          type: Boolean,
          default: false
        },

        // Sidebar theme (available themes: 'white-theme')
        theme: {
          type: String,
          default: "Navy"
        },

        // Disable hover on collapse mode
        disableHover: {
          type: Boolean,
          default: false
        }
      },
      menu: [
        {
          header: true,
          title: "Getting Started",
          hiddenOnCollapse: false
        },
        {
          href: "/",
          title: "Installation",
          icon: "fa fa-download"
        },
        {
          href: "/basic-usage",
          title: "Basic Usage",
          icon: "fa fa-code"
        },
        {
          header: true,
          title: "Usage",
          hiddenOnCollapse: true
        },
        {
          href: "/props",
          title: "Props",
          icon: "fa fa-cogs"
        },
        {
          href: "/events",
          title: "Events",
          icon: "fa fa-bell"
        },
        {
          href: "/styling",
          title: "Styling",
          icon: "fa fa-palette"
        },
        {
          component: separator
        },
        {
          header: true,
          title: "Example",
          hiddenOnCollapse: true
        },
        {
          href: "/disabled",
          title: "Disabled page",
          icon: "fa fa-lock",
          disabled: true
        },
        {
          title: "Badge",
          icon: "fa fa-cog",
          badge: {
            text: "new",
            class: "vsm--badge_default"
          }
        },
        {
          href: "/page",
          title: "Dropdown Page",
          icon: "fa fa-list-ul",
          child: [
            {
              href: "/page/sub-page-1",
              title: "Sub Page 01",
              icon: "fa fa-file-alt"
            },
            {
              href: "/page/sub-page-2",
              title: "Sub Page 02",
              icon: "fa fa-file-alt"
            }
          ]
        },
        {
          title: "Multiple Level",
          icon: "fa fa-list-alt",
          child: [
            {
              title: "page"
            },
            {
              title: "Level 2 ",
              child: [
                {
                  title: "page"
                },
                {
                  title: "Page"
                }
              ]
            },
            {
              title: "Page"
            },
            {
              title: "Another Level 2",
              child: [
                {
                  title: "Level 3",
                  child: [
                    {
                      title: "Page"
                    },
                    {
                      title: "Page"
                    }
                  ]
                }
              ]
            }
          ]
        }
      ],
      collapsed: false,
      themes: [
        {
          name: "Default theme",
          input: ""
        },
        {
          name: "White theme",
          input: "white-theme"
        }
      ],
      selectedTheme: "white-theme",
      isOnMobile: false
    };
  },
  methods: {
    onToggleCollapse(collapsed) {},
    onItemClick(event, item, node) {}
  },
  mounted() {
    this.onResize();
    window.addEventListener("resize", this.onResize);
  },
  methods: {
    onToggleCollapse(collapsed) {
      console.log(collapsed);
      this.collapsed = collapsed;
    },
    onItemClick(event, item, node) {
      console.log("onItemClick");
      // console.log(event)
      // console.log(item)
      // console.log(node)
    },
    onResize() {
      if (window.innerWidth <= 767) {
        this.isOnMobile = true;
        this.collapsed = true;
      } else {
        this.isOnMobile = false;
        this.collapsed = false;
      }
    }
  }
};
</script>

<style scoped>
/* @import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro:400,600'); */
@import url("https://use.fontawesome.com/releases/v5.6.1/css/all.css");

body,
html {
  margin: 0;
  padding: 0;
}

body {
  font-family: "Source Sans Pro", sans-serif;
  font-size: 18px;
  background-color: #f2f4f7;
  color: #262626;
}
.v-sidebar-menu .vsm--link_level-1 .vsm--icon {
  background-color: rgba(15, 39, 62, 1);
}
#demo {
  padding-left: 350px;
  transition: 0.3s ease;
}
#demo.collapsed {
  padding-left: 50px;
}
#demo.onmobile {
  padding-left: 50px;
}

.sidebar-overlay {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-color: #000;
  opacity: 0.5;
  z-index: 900;
}

.demo {
  padding: 50px;
}

.container {
  max-width: 900px;
}

pre {
  font-family: Consolas, monospace;
  color: #000;
  background: #fff;
  border-radius: 2px;
  padding: 15px;
  line-height: 1.5;
  overflow: auto;
}

.v-sidebar-menu .vsm--link_level-1 .vsm--icon {
  background-color: #0f273e;
}
</style>
