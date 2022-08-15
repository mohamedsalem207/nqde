<template>
  <!-- Start of the request page -->
  <div class="request-page d-flex">
    <!-- Requests sidenav -->
    <div class="requests-sidenav p-3">
      <!-- Header data -->
      <div class="header-data">
        <!-- Title -->
        <h5 class="request-title mb-3">إضافة العميل / اسم العميل</h5>

        <!-- Bill number -->
        <h5 class="bill-number mb-3">رقم الفاتورة: #56556</h5>

        <!-- Request type -->
        <h5 class="request-type mb-3">نوع الطلب: سفري</h5>

        <!-- Table number -->
        <h5 class="table-number mb-3">رقم الطاولة: 8</h5>
      </div>
      <!-- End of the header data -->

      <!-- Added requests -->
      <div class="added mb-3 overflow-auto">
        <!-- Request -->
        <div
          v-for="(request, i) in addedRequests"
          :key="i"
          class="request d-flex align-items-center justify-content-between"
        >
          <!-- Request name -->
          <h6
            class="tt request-name mb-0 text-truncate"
            type="button"
            data-bs-toggle="tooltip"
            data-bs-placement="top"
            data-bs-custom-class="custom-tooltip"
            :data-bs-title="request.name"
          >
            {{ request.name }}
          </h6>

          <!-- Control quantity -->
          <div
            class="control-quantity d-flex align-items-center justify-content-center"
          >
            <!-- Control btns -->
            <div class="btns bg-white px-2 ms-3">
              <!-- Increase btn -->
              <button
                @click="
                  request.quantity++
                  request.price = 20 * request.quantity
                "
                class="btn p-0 border-0 fw-bold ms-3"
              >
                <i class="fa-solid fa-plus"></i>
              </button>

              <!-- Number -->
              <span
                class="d-inline-block quantity-number text-center fw-bold"
                >{{ request.quantity }}</span
              >

              <!-- Decrease btn -->
              <button
                @click="
                  request.quantity--
                  request.price = 20 * request.quantity
                "
                :disabled="request.quantity == 0"
                class="btn p-0 border-0 fw-bold me-3"
              >
                <i class="fa-solid fa-minus"></i>
              </button>
            </div>

            <!-- Assign mark -->
            <i class="fa-solid fa-equals"></i>
          </div>

          <!-- Request price -->
          <h6 class="request-price mb-0 text-start ps-3">
            {{ request.price }}
          </h6>
        </div>
      </div>

      <!-- Prices -->
      <div class="prices mb-3">
        <!-- Summation -->
        <div class="d-flex align-items-center justify-content-between mb-3">
          <h5 class="title mb-0 fw-bold">المجموع</h5>

          <h5 class="value mb-0 fw-bold">200 ر.س</h5>
        </div>

        <!-- Discount -->
        <div class="d-flex align-items-center justify-content-between mb-3">
          <h5 class="title mb-0 fw-bold">الخصم</h5>

          <h5 class="value mb-0 fw-bold">0 ر.س</h5>
        </div>

        <!-- Taxes -->
        <div class="d-flex align-items-center justify-content-between mb-4">
          <h5 class="title mb-0 fw-bold">الضرائب</h5>

          <h5 class="value mb-0 fw-bold">200 ر.س</h5>
        </div>
      </div>

      <!-- Total price -->
      <button
        class="btn total-price px-3 border-0 fw-bold w-100 text-white d-flex align-items-center justify-content-between"
      >
        <span class="fs-5 fw-bold">الإجمالي</span>

        <span class="total-price-value">400 ر.س</span>
      </button>
    </div>
    <!-- End of the requests sidenav -->

    <!-- Request content -->
    <div class="classification-content py-2 px-4">
      <!-- Header -->
      <header class="position-relative mb-3 pt-3">
        <!-- Back btn -->
        <button
          @click="$router.go(-1)"
          class="position-absolute top-0 end-0 btn p-0 d-flex align-items-center fs-5 fw-bold border-0"
        >
          <i class="fa-solid fa-chevron-right ms-2"></i>
          <span>رجوع</span>
        </button>

        <!-- Title -->
        <h4 class="title text-center mb-0">اسم التصنيف</h4>
      </header>
      <!-- End of the header -->

      <!-- Search for product -->
      <input
        type="text"
        class="form-control rounded-0 border-0 search mb-3"
        placeholder="بحث المنتجات أو الباركود"
      />

      <!-- Start of the classifications -->
      <div class="classifications-menu d-flex flex-wrap">
        <!-- classification -->
        <div
          v-for="(classification, i) in classifications"
          @click="addClassification(classification)"
          :key="i"
          class="request ms-4"
        >
          <div
            class="classification-content bg-white mb-2 d-flex align-items-center justify-content-center p-2"
          >
            <i :class="classification.icon"></i>
          </div>

          <!-- classification title -->
          <h5 class="classification-title mb-0 text-center fw-bold">
            {{ classification.title }}
          </h5>
        </div>
        <!-- End of the classification title -->
      </div>
      <!-- End of the requests menu -->
    </div>
    <!-- End of the classifications content -->
  </div>
  <!-- End of the request page -->
</template>

<script>
export default {
  name: 'Request',
  data() {
    return {
      classifications: [
        {
          icon: 'fa-solid fa-cake-candles',
          title: 'بان كيك',
        },
        {
          icon: 'fa-solid fa-cake-candles',
          title: 'فرنش توست',
        },
        {
          icon: 'fa-solid fa-cake-candles',
          title: 'حلي عربي',
        },
      ],
      addedRequests: [
        {
          name: 'بان كيك',
          quantity: 1,
          price: 20,
        },
        {
          name: 'بان كيك',
          quantity: 1,
          price: 20,
        },
        {
          name: 'بان كيك',
          quantity: 1,
          price: 20,
        },
      ],
    }
  },
  methods: {
    // Function that add the new classification
    addClassification(item) {
      // Get the classification that match the selected item
      let matchedItem = this.addedRequests.find(
        (request) => request.name == item.title
      )
      if (matchedItem) return
      else {
        // Make a new object variable abd push it to addRequests data property
        let newItem = {
          name: item.title,
          quantity: 1,
          price: 20,
        }
        this.addedRequests.push(newItem)
      }
    },
  },
  mounted() {
    // Calling of bootstrap tooltips
    const tooltips = document.querySelectorAll('.tt')
    if (tooltips) {
      tooltips.forEach((t) => {
        new bootstrap.Tooltip(t)
      })
    }
  },
}
</script>

<style lang="scss" scoped>
.request-page {
  .requests-sidenav {
    height: calc(100vh - 73px);
    width: 310px;
    background-color: #c9c8c8;
    .header-data {
      border-bottom: 2px dashed #707070;
    }
    h5 {
      font-size: 18px;
    }
    .added {
      height: 270px;
      .request {
        padding-block: 13px;
        border-bottom: 2px dashed #707070;
        .request-name,
        .request-price {
          width: 20%;
        }
      }
      .control-quantity {
        width: 60%;
        .btns {
          border-radius: 15px;
        }
        .quantity-number {
          min-width: 20px;
          font-size: 17px;
        }
      }
    }
    .prices {
      border-bottom: 2px dashed #707070;
    }
    .total-price {
      padding-block: 13px;
      background-color: #01416f;
      border-radius: 13px;
    }
    .value,
    .total-price-value {
      direction: ltr !important;
    }
  }
  .classification-content {
    width: calc(100% - 380px);
    header {
      .title {
        font-weight: 500;
      }
    }
    .search {
      padding: 10px;
      font: {
        size: 20px;
        weight: 500;
      }
    }
    .classifications-menu {
      .request {
        height: fit-content;
        cursor: pointer;
        .classification-title,
        .classification-content {
          width: 110px;
        }
        .classification-content {
          height: 90px;
          border-radius: 10px;
          box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
          i {
            font-size: 50px;
          }
        }
      }
    }
  }
}
</style>
