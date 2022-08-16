<template>
  <!-- Start of the sidenav component -->
  <nav class="sidenav position-fixed h-100 end-0 overflow-auto">
    <ul
      class="p-0 m-0 w-100 list-unstyled d-flex d-lg-block justify-content-around"
    >
      <li>
        <NLink
          to="/"
          class="w-100 d-flex align-items-center justify-content-center justify-content-xl-start text-center px-2 text-white text-decoration-none fs-5"
        >
          <i class="fa-solid fa-house ms-xl-5"></i>
          <span class="d-none d-xl-inline">الصفحة الرئيسية</span>
        </NLink>
      </li>
      <li>
        <NLink
          to="/requests"
          class="w-100 d-flex align-items-center justify-content-center justify-content-xl-start text-center px-2 text-white text-decoration-none fs-5"
          :class="$route.name.includes('request') ? 'active' : ''"
          ><i class="fa-solid fa-code-pull-request ms-xl-5"></i>
          <span class="d-none d-xl-inline">الطلبات</span></NLink
        >
      </li>
      <li>
        <NLink
          to="/clients"
          class="w-100 d-flex align-items-center justify-content-center justify-content-xl-start text-center px-2 text-white text-decoration-none fs-5"
          :class="$route.name.includes('client') ? 'active' : ''"
          ><i class="fa-solid fa-user-group ms-xl-5"></i>
          <span class="d-none d-xl-inline">العملاء</span></NLink
        >
      </li>
    </ul>
  </nav>
  <!-- End of the sidenav component -->
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.sidenav {
  width: 315px;
  @media only screen and (max-width: 1400px) {
    width: 290px !important;
  }
  @media only screen and (max-width: 1200px) {
    width: 75px !important;
  }
  @media only screen and (max-width: 992px) {
    bottom: 0;
    top: auto !important;
    left: auto !important;
    right: auto !important;
    height: auto !important;
    width: 100% !important;
  }
  top: 73px;
  background-color: #01416f;
  z-index: 100;
  li {
    @media only screen and (max-width: 992px) {
      width: 150px !important;
    }
    a {
      padding-block: 13px;
      font-weight: 500;
      border-left: 4px solid transparent;
      transition: background 0.1s ease-in-out, border-color 0.1s ease-in-out;
      @media only screen and (max-width: 992px) {
        border-left: 0 !important;
        border-bottom: 4px solid transparent;
      }
      &.nuxt-link-exact-active,
      &.active,
      &:hover {
        background-color: #042f4d;
        border-color: #f20505;
      }
    }
    i {
      font-size: 16px;
      @media only screen and (max-width: 1200px) {
        font-size: 20px !important;
      }
    }
  }
}
</style>
