<template>
  <diV>
    <Header />
    <div
      id="demo"
      :class="[{ collapsed: collapsed }, { onmobile: isOnMobile }]"
    >
      <div class="demo">
        <div class="container">
          <h1>
            vue-sidebar-menuaaaaaaaaaaaaa
            <a
              style="color: #000;text-transform: uppercase;font-size: 14px;font-weight: 400;"
              href="https://github.com/yaminncco/vue-sidebar-menu"
            >
              Github
            </a>
          </h1>
          <div class="control">
            <div class="select">
              <select v-model="selectedTheme">
                              <option
                v-for="(theme, index) in themes"
                :key="index"
                :value="theme.input"
              >
                {{ theme.name }}
              </option>
              </select>
            </div>
          </div>
          <hr style="margin: 50px 0px;border: 1px solid #e3e3e3;" />
          <router-view />
        </div>
        <sidebar-menu
          :menu="menu"
          :collapsed="collapsed"
          :theme="selectedTheme"
          :show-one-child="true"
          @toggle-collapse="onToggleCollapse"
          @item-click="onItemClick"
        />
        <div
          v-if="isOnMobile && !collapsed"
          class="sidebar-overlay"
          @click="collapsed = true"
        />
      </div>
    </div>
  </diV>
</template>

<script>
const separator = {
  template: `<hr style="border-color: rgba(0, 0, 0, 0.1); margin: 20px;">`
};

// import SidebarMenu from "~/components/SidebarMenu";
import Header from "~/components/Header";
import "vue-sidebar-menu/dist/vue-sidebar-menu.css";
export default {
  components: {
    // TheHeader,
    // TheSideNav,
    // TheFooter,
    // NaviVariant,
    // SidebarMenu,
    Header
  },
  name: "App",
  data() {
    return {
      menu: [
        {
          header: true,
          title: "Getting Started",
          hiddenOnCollapse: true
        },
        {
          href: "/",
          title: "Installation",
          icon: "fa fa-file-alt"
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
      selectedTheme: "dark-theme",
      isOnMobile: false
    };
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
    onItemClick(collapsed) {
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

<style>
/* @import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro:400,600'); */
@import url("https://use.fontawesome.com/releases/v5.6.1/css/all.css");
/* @import "./dist/vue-sidebar-menu.css"; */

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

/* .v-sidebar-menu .vsm--icon {
  background-color: #0f273e !important;
} */

.v-sidebar-menu {
  background-color: rgba(15, 39, 62, 1);
  color: #ffffff;
}
/* 
.vsm--link_level-1 .vsm--icon {
    background-color: #0f273e !important;
} */

.v-sidebar-menu .vsm--link_level-1 .vsm--icon {
  background-color: #0f273e !important;
}

.v-sidebar-menu.vsm_white-theme .vsm--link_level-1 .vsm--icon {
  background-color: #ffffff !important;
}

.v-sidebar-menu.vsm_white-theme .vsm--link_hover,
.v-sidebar-menu.vsm_white-theme .vsm--link:hover {
  background-color: #f2f4f7 !important;
}

.v-sidebar-menu.vsm_white-theme
  .vsm--link_level-1.vsm--link_exact-active
  .vsm--icon,
.v-sidebar-menu.vsm_white-theme .vsm--link_level-1.vsm--link_active .vsm--icon {
  color: #0f273e !important;
  /* background-color:  #0f273e !important; */
}
.v-sidebar-menu.vsm_expanded {
  width: 280px;
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
</style>
