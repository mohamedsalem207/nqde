<template>
  <table class="table bg-white text-center">
    <thead>
      <tr class="border-bottom">
        <th v-for="(head, i) in table.header" :key="i" scope="col">
          <span>{{ head.text }}</span>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(row, i) in table.data" :key="i">
        <td v-for="(data, i) in row" :key="i">
          <span
            type="button"
            data-bs-toggle="tooltip"
            data-bs-placement="top"
            data-bs-custom-class="custom-tooltip"
            :data-bs-title="data.text"
            class="tt d-inline-block text-truncate"
          >
            {{ data.text }}
          </span>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'ClientTable',
  props: {
    table: {
      type: Object,
      default: null,
      required: true,
    },
  },
  mounted() {
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
table {
  tr {
    border-color: rgb(112, 112, 112, 0.5) !important;
    &:last-of-type {
      td {
        border: none !important;
      }
    }
    td {
      span {
        width: 225px;
        font-size: 17px;
      }
    }
  }
}
</style>
