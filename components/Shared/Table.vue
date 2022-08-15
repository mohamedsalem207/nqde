<template>
  <table class="table bg-white text-center">
    <thead>
      <tr v-if="allSelected" class="text-end border-bottom">
        <th scope="col">
          <input
            @change="deselectAll"
            checked
            class="form-check-input"
            type="checkbox"
          />
        </th>
        <th>
          <span>محدد</span>
          <span>{{ clientsNumber }}</span>
          <select class="btn me-2 px-2 py-1 border border-1 rounded-3 text-end">
            <option selected disabled value="0">الإجراءات</option>
            <option value="1">إضافة وسوم</option>
            <option value="2">مسح وسوم</option>
            <option value="3">تعديل/مشاهدة</option>
            <option value="4">حذف</option>
          </select>
        </th>
      </tr>
      <tr v-else class="border-bottom">
        <th>
          <input @change="selectAll" class="form-check-input" type="checkbox" />
        </th>
        <th scope="col">الاسم</th>
        <th scope="col">الهاتف</th>
        <th scope="col">البريد الإلكتروني</th>
        <th scope="col">إجمالي الطلبات</th>
        <th scope="col">آخر طلب</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="client in clients"
        @click="$router.push(`/clients/${client.name}`)"
        :key="client.id"
        class="border"
      >
        <th @click="$event.stopPropagation()" scope="row">
          <input
            @change="selectClient($event)"
            class="form-check-input"
            type="checkbox"
            :checked="all"
            ref="selectClient"
          />
        </th>
        <td>{{ client.name }}</td>
        <td>{{ client.phone }}</td>
        <td>{{ client.email }}</td>
        <td>{{ client.totalRequests }}</td>
        <td>{{ client.lastRequest }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'Table',
  props: {
    clients: {
      type: Array,
      required: true,
      default: null,
    },
  },
  data() {
    return {
      allClients: false,
      allSelected: false,
      all: false,
      clientsNumber: 0,
    }
  },
  methods: {
    deselectAll() {
      if (this.$refs.selectClient) {
        if (this.$refs.selectClient.length > 0)
          this.$refs.selectClient.forEach((el) => (el.checked = false))
      }
      this.allSelected = false
      this.all = false
      this.clientsNumber = 0
    },
    selectAll() {
      this.all = true
      this.clientsNumber = this.clients.length
      this.allSelected = true
    },
    selectClient(e) {
      if (e.target.checked) {
        this.allSelected = true
        this.clientsNumber++
      } else {
        if (this.clientsNumber == 1) {
          this.allSelected = false
          this.clientsNumber = 0
        } else this.clientsNumber--
      }
    },
  },
}
</script>

<style lang="scss" scoped>
table {
  border-radius: 7px;
  thead {
    th {
      font-size: 20px;
      border: none !important;
    }
  }
  tbody {
    td {
      font: {
        size: 17px;
        weight: 500;
      }
      cursor: pointer;
    }
  }
  tr {
    border-left: 0 !important;
    border-right: 0 !important;
    border-color: rgb(112, 112, 112, 0.5) !important;
    &:last-of-type {
      border: none !important;
      td,
      th {
        border: none !important;
      }
    }
  }
  input {
    cursor: pointer;
    &:checked {
      background-color: #01416f !important;
    }
  }
  select {
    border: 1px solid #01416f !important;
  }
}
</style>
