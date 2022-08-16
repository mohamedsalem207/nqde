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
          <div class="d-flex">
            <span>محدد</span>
            <span>{{ clientsNumber }}</span>
            <select
              class="btn me-2 px-2 py-1 border border-1 rounded-3 text-end"
            >
              <option selected disabled value="0">الإجراءات</option>
              <option value="1">إضافة وسوم</option>
              <option value="2">مسح وسوم</option>
              <option value="3">تعديل/مشاهدة</option>
              <option value="4">حذف</option>
            </select>
          </div>
        </th>
      </tr>
      <tr v-else class="border-bottom">
        <th>
          <input @change="selectAll" class="form-check-input" type="checkbox" />
        </th>
        <th scope="col" class="text-truncate">الاسم</th>
        <th scope="col" class="text-truncate">الهاتف</th>
        <th scope="col" class="text-truncate">البريد الإلكتروني</th>
        <th scope="col" class="text-truncate">إجمالي الطلبات</th>
        <th scope="col" class="text-truncate">آخر طلب</th>
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
        <td class="text-truncate">{{ client.name }}</td>
        <td class="text-truncate">{{ client.phone }}</td>
        <td class="text-truncate">{{ client.email }}</td>
        <td class="text-truncate">{{ client.totalRequests }}</td>
        <td class="text-truncate">{{ client.lastRequest }}</td>
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
    // Function that deselect all clients
    deselectAll() {
      // Get all check inputs in the table body
      if (this.$refs.selectClient) {
        // Set checked attribute to false
        if (this.$refs.selectClient.length > 0)
          this.$refs.selectClient.forEach((el) => (el.checked = false))
      }
      // Set allSelected data property to false
      this.allSelected = false
      // Set all property data to false
      this.all = false
      // Set clientsNumber data property to 0
      this.clientsNumber = 0
    },
    // Function that select all clients
    selectAll() {
      // Set all data property to true
      this.all = true
      // Set clientsNumber data property to be the number of all clients
      this.clientsNumber = this.clients.length
      // Set allSelected data property to true
      this.allSelected = true
    },
    selectClient(e) {
      // Check that the client is selected
      if (e.target.checked) {
        // Set allSelected data property to true
        this.allSelected = true
        // Increase the value of clientsNumber data property
        this.clientsNumber++
      } else {
        // Check if the clientsNumber data property if equal 1
        if (this.clientsNumber == 1) {
          // Set allSelected data property to false
          this.allSelected = false
          // Set clientsNumber data property to 0
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
