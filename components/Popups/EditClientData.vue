<template>
  <!-- Start of the edit-client-data popup -->
  <div
    class="edit-client-data position-fixed top-0 start-0 w-100 h-100 p-3 d-flex align-items-center justify-content-center"
  >
    <!-- Start of the popup content  -->
    <div class="popup-content rounded-3 overflow-auto">
      <!-- Popup title -->
      <h5 class="title p-3 bg-white fw-bold">تعديل بيانات العميل</h5>

      <!-- Filter form -->
      <form @submit.prevent="apply">
        <!-- Name -->
        <div class="name mb-2 px-3">
          <label class="form-label d-flex align-items-end" for="name">
            <span>الاسم</span>
            <span class="required">*</span>
          </label>
          <input
            type="text"
            v-model="name"
            id="name"
            class="form-control me-1"
            name="name"
            placeholder=""
          />
        </div>

        <!-- Phone -->
        <div class="phone mb-2 px-3">
          <label class="form-label" for="phone"
            ><span>الهاتف</span> <span class="required">*</span></label
          >
          <input
            type="number"
            v-model="phone"
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
            type="email"
            v-model="email"
            id="email"
            class="form-control me-1"
            name="email"
            placeholder=""
          />
        </div>

        <!-- Tags -->
        <div class="date mb-2 px-3">
          <label class="form-label" for="date">تاريخ الميلاد</label>
          <input type="date" v-model="date" id="date" class="form-control" />
        </div>

        <!-- Sex -->
        <div class="Sex mb-2 px-3">
          <label class="form-label" for="have-requests">الجنس</label>
          <select id="have-requests" v-model="sex" class="form-control">
            <option value="0" selected disabled>حدد النوع</option>
            <option value="1">ذكر</option>
            <option value="2">أنثي</option>
          </select>
        </div>

        <!-- Term -->
        <div class="term mb-2 px-3">
          <label class="form-label" for="term">حد الحساب الآجل</label>
          <div class="form-control d-flex justify-content-between p-0">
            <input
              type="number"
              v-model="term"
              id="term"
              class="form-control border-0"
              :style="{ width: '79%' }"
            />

            <input
              type="text"
              value="SAR"
              class="form-control text-center border-0"
              readonly
              :style="{ width: '18%' }"
            />
          </div>
        </div>

        <!-- Btns -->
        <div
          class="btns w-100 d-flex align-items-center justify-content-between mt-4 py-3 px-3 bg-white"
        >
          <!-- Reset-btn -->
          <button class="btn reset-btn text-white border border-2">
            حذف العميل
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
  <!-- End of the edit-client-data popup -->
</template>

<script>
export default {
  name: 'EditClientData',
  data() {
    return {
      name: 'علي الأسمري',
      phone: '01015591833',
      email: 'alialasmaree2022@gmail.com',
      date: '',
      sex: 1,
      term: 500,
    }
  },
}
</script>

<style lang="scss" scoped>
.edit-client-data {
  background-color: rgba(0, 0, 0, 0.7);
  z-index: 102;
  .popup-content {
    max-height: 100%;
    width: 35%;
    background-color: #fafafa;
    form {
      .required {
        color: #f20505;
        font-size: 20px;
      }
      .term {
        input {
          font-size: 18px;
        }
        input[readonly] {
          &:focus {
            box-shadow: none;
          }
        }
      }
    }
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
