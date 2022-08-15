<template>
  <!-- Start of the clients page -->
  <div class="clients">
    <!-- Start of the header -->
    <header class="bg-white d-flex justify-content-between pt-2 px-2">
      <!-- Content -->
      <div class="content pe-5">
        <!-- Title -->
        <h4 class="title fw-bold mb-4">العملاء</h4>

        <!-- Menu -->
        <ul class="list-unstyled d-flex p-0 m-0">
          <li class="ms-4">
            <button class="position-relative active btn border-0 p-0 pb-2">
              الكل
            </button>
          </li>
          <li class="ms-4">
            <button class="position-relative btn border-0 p-0 pb-2">
              لديه طلبات
            </button>
          </li>
          <li class="ms-4">
            <button class="position-relative btn border-0 p-0 pb-2">
              فى القائمة السوداء
            </button>
          </li>
          <li class="ms-4">
            <button class="position-relative btn border-0 p-0 pb-2">
              محذوف
            </button>
          </li>
        </ul>
      </div>
      <!-- End of the content -->

      <!-- Btns -->
      <div class="btns">
        <select class="btn border-0 text-white ms-2 px-3 py-2">
          <option value="0" selected disabled>استيراد/تصدير</option>
          <option value="1">استيراد</option>
          <option value="2">تصدير</option>
        </select>

        <button class="btn border-0 text-white px-3 py-2">إضافة عميل</button>
      </div>
    </header>
    <!-- End of the header -->

    <!-- Clients content -->
    <div class="clients-content pt-3 ps-3 pe-5">
      <!-- Calling of the filter popup -->
      <PopupsFilter v-if="filter" @close="filter = false" />

      <div class="table-btns mb-4 d-flex justify-content-end ps-3">
        <button
          class="ms-2 btn border-0 bg-white d-flex align-items-center justify-content-center"
        >
          <i class="fs-5 fa-solid fa-rotate-right"></i>
        </button>

        <button
          @click="filter = true"
          class="btn border-0 bg-white d-flex align-items-center justify-content-center"
        >
          <i class="fs-5 fa-solid fa-filter ms-2"></i>
          <span class="fw-bold">تصفية</span>
        </button>
      </div>

      <!-- Calling of the table component -->
      <SharedTable :clients="clients" />
    </div>
    <!-- End of the clients content -->
  </div>
  <!-- End of the clients page -->
</template>

<script>
export default {
  name: 'Clients',
  data() {
    return {
      filter: false,
      clients: [
        {
          id: 1,
          name: 'علي الأسمري',
          phone: '01015591833',
          email: 'aliasmareeeeeeefj@gmail.com',
          totalRequests: 0,
          lastRequest: '02/02/2022 05:00 م',
        },
        {
          id: 2,
          name: 'علي الأسمري',
          phone: '01015591833',
          email: 'aliasmareeeeeeefj@gmail.com',
          totalRequests: 0,
          lastRequest: '02/02/2022 05:00 م',
        },
        {
          id: 3,
          name: 'علي الأسمري',
          phone: '01015591833',
          email: 'aliasmareeeeeeefj@gmail.com',
          totalRequests: 0,
          lastRequest: '02/02/2022 05:00 م',
        },
        {
          id: 4,
          name: 'علي الأسمري',
          phone: '01015591833',
          email: 'aliasmareeeeeeefj@gmail.com',
          totalRequests: 0,
          lastRequest: '02/02/2022 05:00 م',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.clients {
  li {
    button {
      font-size: 17px;
      &::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        height: 2px;
        width: 100%;
        transition: background 0.2s ease-in-out;
      }
      &:hover,
      &.active {
        &::after {
          background-color: #01416f;
        }
      }
    }
  }
  .btns {
    select,
    button {
      font-weight: 500;
      background-color: #01416f;
      border-radius: 4.5px;
    }
  }
  .table-btns {
    button {
      box-shadow: 0 3px 6px rgba(0, 0, 0, 0.2);
    }
  }
}
</style>
