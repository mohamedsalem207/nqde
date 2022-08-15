<template>
  <!-- Start of the sidenav component -->
  <nav class="sidenav position-fixed h-100 end-0 overflow-auto">
    <ul class="p-0 m-0 w-100 list-unstyled">
      <li>
        <NLink
          to="/"
          class="w-100 d-flex align-items-center text-center px-2 text-white text-decoration-none fs-5"
        >
          <i class="fa-solid fa-house"></i>
          <span>الصفحة الرئيسية</span>
        </NLink>
      </li>
      <li>
        <NLink
          to="/requests"
          class="w-100 d-flex align-items-center text-center px-2 text-white text-decoration-none fs-5"
          :class="$route.name.includes('request') ? 'active' : ''"
          ><i class="fa-solid fa-code-pull-request"></i>
          <span>الطلبات</span></NLink
        >
      </li>
      <li>
        <NLink
          to="/clients"
          class="w-100 d-flex align-items-center text-center px-2 text-white text-decoration-none fs-5"
          :class="$route.name.includes('client') ? 'active' : ''"
          ><i class="fa-solid fa-user-group"></i> <span>العملاء</span></NLink
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
  top: 73px;
  background-color: #01416f;
  z-index: 100;
  a {
    padding-block: 13px;
    font-weight: 500;
    border-left: 4px solid transparent;
    transition: background 0.1s ease-in-out, border-color 0.1s ease-in-out;
    &.nuxt-link-exact-active,
    &.active,
    &:hover {
      background-color: #042f4d;
      border-left-color: #f20505;
    }
    i {
      font-size: 16px;
      margin-inline-end: 70px;
    }
  }
}
</style>
