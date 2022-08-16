<template>
  <!-- Start of the client page -->
  <div class="client">
    <!-- Start of the header -->
    <header
      class="bg-white d-flex flex-column flex-md-row justify-content-between pt-2 pb-4 px-2 mb-5"
    >
      <!-- Content -->
      <div class="content mb-3 mb-md-0">
        <!-- Calling of the EditClientData component -->
        <PopupsEditClientData
          v-if="editClientData"
          @close="editClientData = false"
        />

        <!-- Back btn -->
        <button
          @click="$router.go(-1)"
          class="fs-5 fw-bold btn mb-1 border-0 p-0 d-flex align-items-center"
        >
          <i class="fa-solid fa-chevron-right ms-2"></i>
          <span>رجوع</span>
        </button>

        <!-- Client name -->
        <h4 class="client-name mb-0">{{ $route.params.client }}</h4>
      </div>
      <!-- End of the content -->

      <!-- Btns -->
      <div class="btns">
        <select class="btn border-0 ms-2 px-3 py-2">
          <option value="0" selected disabled>إجراءات آخرى</option>
          <option value="1">استيراد</option>
          <option value="2">تصدير</option>
        </select>

        <button
          @click="editClientData = true"
          class="btn border-0 text-white px-3 py-2"
        >
          تعديل العميل
        </button>
      </div>
    </header>
    <!-- End of the header -->

    <!-- Content -->
    <div class="content px-lg-5 px-2">
      <!-- Client stats -->
      <div class="client-stats">
        <div class="row px-0 mx-0 flex-wrap">
          <!-- Stat -->
          <div class="stat col-lg-4 px-3">
            <!-- Stat-content -->
            <div class="stat-content bg-white p-2">
              <!-- Stat title -->
              <h5 class="mb-3">الطلبات المغلقة</h5>

              <!-- Stat-number -->
              <h4
                class="d-flex align-items-center justify-content-center stat-number mb-0 text-center"
              >
                0
              </h4>
            </div>
          </div>

          <!-- Stat -->
          <div class="stat col-lg-4 px-3">
            <!-- Stat-content -->
            <div class="stat-content bg-white p-2">
              <!-- Stat title -->
              <h5 class="mb-3">إجمالي المدفوعات (SAR)</h5>

              <!-- Stat-number -->
              <h4
                class="d-flex align-items-center justify-content-center stat-number mb-0 text-center"
              >
                0
              </h4>
            </div>
          </div>

          <!-- Stat -->
          <div class="stat col-lg-4 px-3">
            <!-- Stat-content -->
            <div class="stat-content bg-white p-2">
              <!-- Stat title -->
              <h5 class="mb-3">إجمالي الخصومات (SAR)</h5>

              <!-- Stat-number -->
              <h4
                class="d-flex align-items-center justify-content-center stat-number mb-0 text-center"
              >
                0
              </h4>
            </div>
          </div>

          <!-- Stat -->
          <div class="stat col-lg-4 px-3">
            <!-- Stat-content -->
            <div class="stat-content bg-white p-2">
              <!-- Stat title -->
              <h5 class="mb-3">إجمالي الخصومات (SAR)</h5>

              <!-- Stat-number -->
              <h4
                class="d-flex align-items-center justify-content-center stat-number mb-0 text-center"
              >
                0
              </h4>
            </div>
          </div>

          <!-- Stat -->
          <div class="stat col-lg-4 px-3">
            <!-- Stat-content -->
            <div class="stat-content bg-white p-2">
              <!-- Stat title -->
              <h5 class="mb-3">المنتج المفضل</h5>

              <!-- Stat-number -->
              <h4
                class="d-flex align-items-center justify-content-center stat-number mb-0 text-center"
              >
                -
              </h4>
            </div>
          </div>

          <!-- Stat -->
          <div class="stat col-lg-4 px-3">
            <!-- Stat-content -->
            <div class="stat-content bg-white p-2">
              <!-- Stat title -->
              <h5 class="mb-3">الفرع المفضل</h5>

              <!-- Stat-number -->
              <h4
                class="d-flex align-items-center justify-content-center stat-number mb-0 text-center"
              >
                -
              </h4>
            </div>
          </div>
        </div>
      </div>
      <!-- End of the client stats -->

      <!-- Client info -->
      <div class="client-info py-3 px-2 px-md-4 bg-white mx-3 mb-4">
        <div class="row justify-content-between px-0 mx-0 mb-4">
          <div class="col-lg-6 ps-5 mb-4 mb-md-0">
            <h4 class="fw-bold mb-3">الاسم</h4>

            <h5 class="mb-0 pb-2 border-bottom border-2">علي الأسمري</h5>
          </div>

          <div class="col-lg-6 ps-5 mb-4 mb-md-0">
            <h4 class="fw-bold mb-3">البريد الإلكتروني</h4>

            <h5 class="mb-0 pb-2 border-bottom border-2">
              alialasmaree2022@gmail.com
            </h5>
          </div>
        </div>

        <div class="row justify-content-between px-0 mx-0 mb-4">
          <div class="col-lg-6 ps-5 mb-4 mb-md-0">
            <h4 class="fw-bold mb-3">الهاتف</h4>

            <h5 class="mb-0 pb-2 border-bottom border-2">01015591833</h5>
          </div>

          <div class="col-lg-6 ps-5 mb-4 mb-md-0">
            <h4 class="fw-bold mb-3">برنامج الولاء</h4>

            <h5 class="mb-0 pb-2 border-bottom border-2">غير مفعل</h5>
          </div>
        </div>

        <div class="row justify-content-between px-0 mx-0 mb-4">
          <div class="col-lg-6 ps-5 mb-4 mb-md-0">
            <h4 class="fw-bold mb-3 me-2">الحسابات الآجله</h4>

            <h5 class="mb-0 pb-2 border-bottom border-2">غير مفعل</h5>
          </div>

          <div class="col-lg-6 ps-5 mb-4 mb-md-0">
            <h4 class="fw-bold mb-3 me-2">القائمة السوداء</h4>

            <h5 class="mb-0 pb-2 border-bottom border-2">لا</h5>
          </div>
        </div>
      </div>
      <!-- End of the client info -->

      <!-- Tags -->
      <div class="tags mx-3 mb-5">
        <!-- Start of the header -->
        <header
          class="mb-3 d-flex flex-column flex-md-row justify-content-between"
        >
          <h2 class="me-3 mb-3 mb-md-0 fw-bold">الوسوم</h2>

          <button class="btn border-0 text-white px-2 px-md-4">
            إضافة وسوم
          </button>
        </header>
        <!-- End of the header -->

        <!-- Tags content -->
        <div class="tags-content bg-white py-3 px-2 px-md-4">
          <h5 class="empty text-end text-md-center">
            يمكنك إضافة وسم لهذا العميل لغرض التصفية و تعيين العروض الترويجية.
          </h5>

          <span
            class="special d-inline-block pt-0 pb-1 px-2 border border-2 rounded-1"
            >عميل مميز</span
          >
        </div>
        <!-- End of the tags content -->
      </div>
      <!-- End of the tags -->

      <!-- Title -->
      <div class="tags mx-3 mb-3">
        <!-- Start of the header -->
        <header
          class="mb-3 d-flex flex-column flex-md-row justify-content-between"
        >
          <h2 class="me-3 mb-3 mb-md-0 fw-bold">العناوين</h2>

          <button class="btn border-0 text-white px-4">إضافة عنوان</button>
        </header>
        <!-- End of the header -->

        <!-- Tags content -->
        <div class="tags-content bg-white py-3 px-4">
          <div class="table-responsive">
            <SharedClientTable :table="titleTable" />
          </div>
        </div>
        <!-- End of the tags content -->
      </div>
      <!-- End of the title -->

      <!-- Requests -->
      <div class="tags mx-3 mb-5">
        <!-- Start of the header -->
        <header
          class="mb-3 d-flex flex-column flex-md-row justify-content-between"
        >
          <h2 class="me-3 mb-3 mb-md-0 fw-bold">الطلبات</h2>

          <button class="btn border-0 text-white px-4">إضافة طلب</button>
        </header>
        <!-- End of the header -->

        <!-- Tags content -->
        <div class="tags-content bg-white py-3 px-4">
          <div class="table-responsive">
            <SharedClientTable :table="requestsTable" />
          </div>
        </div>
        <!-- End of the tags content -->
      </div>
      <!-- End of the title -->

      <!-- Transaction -->
      <div class="tags mx-3 mb-5">
        <!-- Start of the header -->
        <header
          class="mb-3 d-flex flex-column flex-md-row justify-content-between"
        >
          <h2 class="me-3 mb-3 mb-md-0 fw-bold">معاملات الحساب الآجل</h2>

          <button class="btn border-0 text-white px-4">إضافة دفعة</button>
        </header>
        <!-- End of the header -->

        <!-- Tags content -->
        <div class="tags-content bg-white py-3 px-4">
          <div class="table-responsive">
            <SharedClientTable :table="transactionTable" />
          </div>
        </div>
        <!-- End of the tags content -->
      </div>
      <!-- End of the title -->
    </div>
    <!-- End of the content -->
  </div>
  <!-- End of the client page -->
</template>

<script>
export default {
  name: 'Client',
  data() {
    return {
      editClientData: false,
      titleTable: {
        header: [
          {
            text: 'الاسم',
          },
          {
            text: 'الوصف',
          },
          {
            text: 'منطقة التوصيل',
          },
          {
            text: 'تم الإنشاء',
          },
        ],
        data: [
          [
            {
              text: 'منزل العميل',
            },
            {
              text: 'أمام سوبر ماركت أمام سوبر ماركت أمام سوبر ماركت',
            },
            {
              text: 'القاهرة - مدينة نصر',
            },
            {
              text: '02/02/2022 04:00 ص',
            },
          ],
        ],
      },
      requestsTable: {
        header: [
          {
            text: 'المنتج',
          },
          {
            text: 'السعر',
          },
          {
            text: 'الفرع',
          },
          {
            text: 'تم الإنشاء',
          },
        ],
        data: [
          [
            {
              text: 'برجر لحم',
            },
            {
              text: '15 SAR',
            },
            {
              text: 'فرع العوالي',
            },
            {
              text: '02/02/2022 04:00 ص',
            },
          ],
          [
            {
              text: 'برجر لحم',
            },
            {
              text: '15 SAR',
            },
            {
              text: 'فرع العوالي',
            },
            {
              text: '02/02/2022 04:00 ص',
            },
          ],
        ],
      },
      transactionTable: {
        header: [
          {
            text: 'النوع',
          },
          {
            text: 'القيمة',
          },
          {
            text: 'المنشئ',
          },
          {
            text: 'التاريخ',
          },
        ],
        data: [
          [
            {
              text: 'دفعه للحساب',
            },
            {
              text: '15 SAR',
            },
            {
              text: 'Ali Salamah',
            },
            {
              text: '02/02/2022 04:00 ص',
            },
          ],
        ],
      },
    }
  },
}
</script>

<style lang="scss" scoped>
.client {
  .btns {
    select,
    button {
      font-weight: 500;
      border-radius: 4.5px;
    }
    button {
      background-color: #01416f;
    }
    select {
      box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
    }
  }
  .client-stats {
    .stat {
      margin-bottom: 31px;
      .stat-content {
        .stat-number {
          height: 70px;
        }
      }
    }
  }
  .tags {
    button {
      background-color: #01416f;
      font-weight: 500;
    }
    .tags-content {
      h5.empty {
        font-size: 23px;
      }
      .special {
        font-size: 21px;
        border-color: #01416f !important;
      }
    }
  }
  .stat-content,
  .client-info,
  .tags-content {
    border-radius: 10px;
  }
}
</style>
