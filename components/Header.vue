<template>
  <nav
    class="navbar navbar is-fixed-top"
    role="navigation"
    aria-label="main navigation"
  >
    <div class="navbar-end">
      
      <div class="navbar-item">
        <Logo />
      </div>
    </div>
  </nav>
</template>
<script>
export default {
  data() {
    return {
    }
  }
}
</script>

<style>
.menu {
  padding: 0;
  background-color: rgba(15, 39, 62, 1);
}

.navbar-brand {
  background-color: rgba(15, 39, 62, 1);
}

.navbar {
  background-color: rgba(15, 39, 62, 1);
}
.menu li {
  display: inline-block;
  padding: 5px;
}
</style>