<template>
  <!-- Start of the requests page -->
  <div class="requests d-flex">
    <!-- Requests sidenav -->
    <div class="requests-sidenav bg-white p-3"></div>
    <!-- End of the requests sidenav -->

    <!-- Start of the requests menu -->
    <div class="requests-menu d-flex flex-wrap p-4">
      <!-- Request -->
      <div
        @click="$router.push(`requests/${request.id}`)"
        v-for="request in requests"
        :key="request.id"
        class="request ms-4"
      >
        <div
          class="request-content bg-white mb-2 d-flex align-items-center justify-content-center p-2"
        >
          <i :class="request.icon"></i>
        </div>

        <!-- Request title -->
        <h5 class="request-title mb-0 text-center fw-bold">
          {{ request.title }}
        </h5>
      </div>
      <!-- Title -->
      <!-- End of the request -->
    </div>
    <!-- End of the requests menu -->
  </div>
  <!-- End of the requests page -->
</template>

<script>
export default {
  name: 'Requests',
  data() {
    return {
      requests: [
        {
          id: 1,
          icon: 'fa-solid fa-mug-hot',
          title: 'ساخن',
        },
        {
          id: 2,
          icon: 'fa-solid fa-cake-candles',
          title: 'حلويات',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.requests {
  .requests-sidenav {
    height: calc(100vh - 73px);
    width: 310px;
  }
  .requests-menu {
    .request {
      height: fit-content;
      cursor: pointer;
      .request-content {
        height: 90px;
        width: 110px;
        border-radius: 10px;
        box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
        i {
          font-size: 50px;
        }
      }
    }
  }
}
</style>
