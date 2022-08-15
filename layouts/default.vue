<template>
  <div>
    <!-- Calling of the navbar component -->
    <NavigationNavbar />

    <!-- Calling of the sidenav component -->
    <NavigationSideNav />

    <!-- Current route page -->
    <Nuxt />
  </div>
</template>

<script>
export default {
  name: 'Default',
  head() {
    return {
      htmlAttrs: {
        dir: 'rtl',
      },
    }
  },
}
</script>
