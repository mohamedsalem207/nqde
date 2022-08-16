<template>
  <!-- Start of the request page -->
  <div class="request-page d-flex">
    <!-- Requests sidenav -->
    <div class="requests-sidenav p-3" :class="show ? 'show' : ''">
      <!-- Mobile show menu -->
      <div class="show-menu mb-3">
        <button
          @click="show = !show"
          class="show-menu-btn border-0 d-flex align-items-center justify-content-center btn bg-white p-0"
        >
          <i
            class="fs-1 fa-solid"
            :class="show ? 'fa-angle-down' : 'fa-angle-up'"
          ></i>
        </button>
      </div>

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
                @click="increaseQuantity(request)"
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
                @click="decreaseQuantity(request)"
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

          <h5 class="value mb-0 fw-bold">{{ summation }} ر.س</h5>
        </div>

        <!-- Discount -->
        <div class="d-flex align-items-center justify-content-between mb-3">
          <h5 class="title mb-0 fw-bold">الخصم</h5>

          <h5 class="value mb-0 fw-bold">{{ discount }} ر.س</h5>
        </div>

        <!-- Taxes -->
        <div class="d-flex align-items-center justify-content-between mb-4">
          <h5 class="title mb-0 fw-bold">الضرائب</h5>

          <h5 class="value mb-0 fw-bold">{{ taxes }} ر.س</h5>
        </div>
      </div>

      <!-- Total price -->
      <button
        class="btn total-price px-3 border-0 fw-bold w-100 text-white d-flex align-items-center justify-content-between"
      >
        <span class="fs-5 fw-bold">الإجمالي</span>

        <span class="total-price-value">{{ calcTotal }} ر.س</span>
      </button>
    </div>
    <!-- End of the requests sidenav -->

    <!-- Request container -->
    <div class="classification-container py-2 px-4">
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
        <h4 class="title text-center mb-0 mt-3">اسم التصنيف</h4>
      </header>
      <!-- End of the header -->

      <!-- Search for product -->
      <input
        type="text"
        class="form-control rounded-0 border-0 search mb-3"
        placeholder="بحث المنتجات أو الباركود"
      />

      <!-- Start of the classifications -->
      <div
        class="classifications-menu d-flex flex-wrap flex-column justify-content-center justify-content-md-start flex-sm-row"
      >
        <!-- classification -->
        <div
          v-for="(classification, i) in classifications"
          @click="addClassification(classification)"
          :key="i"
          class="request ms-0 mb-3 ms-sm-4 d-flex flex-column justify-content-center justify-content-sm-start align-items-center d-sm-block"
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
      show: false,
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
      ],
      summation: 0,
      discount: 0,
      taxes: 10,
    }
  },
  computed: {
    // Compute the total price for the bill
    calcTotal() {
      // Get all items price
      let prices = this.addedRequests.map((item) => {
        return +item.price
      })
      // Calc the summation of the prices
      let totalPrices = prices.reduce((acc, current) => {
        return +acc + +current
      }, 0)
      // Get the mathematical operation that calc total
      let total = +totalPrices + +this.taxes - +this.discount
      // Check if total greater than 0
      if (total > 0) return total
      // return taxes if total less than 0
      else return +this.taxes
    },
  },
  methods: {
    // Function that call bootstrap tooltip
    bootstrapTooltip() {
      // Calling of bootstrap tooltips
      let tooltips = document.querySelectorAll('.tt')
      if (tooltips) {
        tooltips.forEach((t) => {
          return new bootstrap.Tooltip(t)
        })
      }
    },
    // Function that add the new classification
    addClassification(item) {
      // Get the classification that match the selected item
      let matchedItem = this.addedRequests.find(
        (request) => request.name == item.title
      )
      // Set show data property to true
      this.show = true
      if (matchedItem) return
      else {
        // Make a new object variable abd push it to addRequests data property
        let newItem = {
          name: item.title,
          quantity: 1,
          price: 20,
        }
        this.addedRequests.push(newItem)
        // Calling of the bootstrapTooltip function
        setTimeout(() => {
          this.bootstrapTooltip()
        }, 10)
      }
    },
    // Function that increase the quantity of request
    increaseQuantity(item) {
      // Get the item from addedRequests data that match item parameter
      let matchedItem = this.addedRequests.find(
        (request) => request.name == item.name
      )
      // Increase the quantity of the matchedItem by 1
      matchedItem.quantity++
      // Recalculate the price of the item
      matchedItem.price = 20 * matchedItem.quantity
    },
    // Function that decrease the quantity of the request
    decreaseQuantity(item) {
      // Get the item from addedRequests data that match item parameter
      let matchedItem = this.addedRequests.find(
        (request) => request.name == item.name
      )
      // Increase the quantity of the matchedItem by 1
      matchedItem.quantity--
      // Recalculate the price of the item
      matchedItem.price = 20 * matchedItem.quantity
    },
  },
  mounted() {
    // Calling of the bootstrapTooltip function
    this.bootstrapTooltip()
  },
}
</script>

<style lang="scss" scoped>
.request-page {
  .requests-sidenav {
    height: calc(100vh - 73px);
    @media only screen and (max-width: 600px) {
      position: fixed;
      bottom: -76%;
      width: 100%;
      z-index: 1;
    }
    width: 310px;
    background-color: #c9c8c8;
    transition: bottom 0.3s ease-in-out;
    &.show {
      bottom: 0 !important;
    }
    .show-menu {
      display: none;
      @media only screen and (max-width: 600px) {
        display: block;
      }
      .show-menu-btn {
        height: 50px;
        width: 50px;
        border-radius: 50%;
      }
    }
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
  .classification-container {
    width: calc(100% - 380px);
    @media only screen and (max-width: 992px) {
      width: calc(100% - 310px) !important;
    }
    @media only screen and (max-width: 600px) {
      width: 100% !important;
    }
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
        @media only screen and (max-width: 767px) {
          width: 100% !important;
        }
        cursor: pointer;
        .classification-title,
        .classification-content {
          width: 110px;
          @media only screen and (max-width: 767px) {
            width: 95% !important;
          }
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
