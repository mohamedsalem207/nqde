<template>
  <!-- Start of the filter popup -->
  <div
    class="filter-popup position-fixed top-0 start-0 w-100 h-100 p-3 d-flex align-items-center justify-content-center"
  >
    <!-- Start of the popup content  -->
    <div class="popup-content h-100 rounded-3 overflow-auto">
      <!-- Popup title -->
      <h5 class="title p-3 bg-white fw-bold">تصفيه</h5>

      <!-- Filter form -->
      <form @submit.prevent="apply">
        <!-- Name -->
        <div class="name mb-2 px-3">
          <label class="form-label" for="name">الاسم</label>
          <input
            type="text"
            id="name"
            class="form-control me-1"
            name="name"
            placeholder=""
          />
        </div>

        <!-- Phone -->
        <div class="phone mb-2 px-3">
          <label class="form-label" for="phone">الهاتف</label>
          <input
            type="number"
            id="phone"
            class="form-control me-1"
            name="phone"
            placeholder=""
          />
        </div>

        <!-- Email -->
        <div class="email mb-2 px-3">
          <label class="form-label" for="email">البريد الإلكتروني</label>
          <input
            type="number"
            id="email"
            class="form-control me-1"
            name="email"
            placeholder=""
          />
        </div>

        <!-- Tags -->
        <div class="tags mb-2 px-3">
          <label class="form-label" for="tags">الوسوم</label>
          <select id="tags" class="form-control">
            <option value="0" selected disabled>اختر</option>
          </select>
        </div>

        <!-- Have requests -->
        <div class="have-requests mb-2 px-3">
          <label class="form-label" for="have-requests">لديه طلبات</label>
          <select id="have-requests" class="form-control">
            <option value="0" selected disabled>نعم / لا</option>
            <option value="1">نعم</option>
            <option value="2">لا</option>
          </select>
        </div>

        <!-- Black list -->
        <div class="black-list mb-2 px-3">
          <label class="form-label" for="black-list">في القائمة السوداء</label>
          <select id="black-list" class="form-control">
            <option value="0" selected disabled>نعم / لا</option>
            <option value="1">نعم</option>
            <option value="2">لا</option>
          </select>
        </div>

        <!-- Term -->
        <div class="term mb-2 px-3">
          <label class="form-label" for="term">الحساب الآجل مفعل</label>
          <select id="term" class="form-control">
            <option value="0" selected disabled>نعم / لا</option>
            <option value="1">نعم</option>
            <option value="2">لا</option>
          </select>
        </div>

        <!-- Deleted -->
        <div class="deleted mb-2 px-3">
          <label class="form-label" for="deleted">محذوف</label>
          <select id="deleted" class="form-control">
            <option value="0" selected disabled>نعم / لا</option>
            <option value="1">نعم</option>
            <option value="2">لا</option>
          </select>
        </div>

        <!-- Updated -->
        <div class="updated px-3">
          <label class="form-label" for="updated">تم تحديثه بعد</label>
          <input type="date" class="form-control" />
        </div>

        <!-- Btns -->
        <div
          class="btns w-100 d-flex align-items-center justify-content-between mt-4 py-3 px-3 bg-white"
        >
          <!-- Reset-btn -->
          <button class="btn reset-btn text-white border border-2" type="reset">
            إعادة الضبط
          </button>

          <!-- Submit-btns -->
          <div class="submit-btns">
            <!-- Close popup -->
            <button
              @click="
                $event.preventDefault()
                $emit('close')
              "
              class="btn close-btn border border-2 ms-2"
            >
              إغلاق
            </button>

            <!-- Apply btn -->
            <button class="btn apply-btn border border-2 text-white">
              تطبيق
            </button>
          </div>
        </div>
      </form>
    </div>
    <!-- End of the popup content -->
  </div>
  <!-- End of the filter popup -->
</template>

<script>
export default {
  name: 'FilterPopup',
  methods: {
    apply() {
      console.log('Good')
    },
  },
}
</script>

<style lang="scss" scoped>
.filter-popup {
  background-color: rgba(0, 0, 0, 0.7);
  z-index: 102;
  .popup-content {
    width: 35%;
    background-color: #fafafa;
    .btns {
      .reset-btn {
        font-weight: 500;
        background-color: #f20505;
        border-color: #f20505 !important;
      }
    }
    .submit-btns {
      button {
        width: 100px;
        font-weight: 500;
      }
      .close-btn {
        border-color: #707070 !important;
      }
      .apply-btn {
        background-color: #01416f;
        border-color: transparent !important;
      }
    }
  }
}
</style>
