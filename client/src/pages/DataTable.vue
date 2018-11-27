<template>
    <table class="data-table">
        <thead>
        <tr>
            <th
                    v-for="column of columns"
                    :key="column.field"
                    :style="{width: column.width}">
                {{ column.caption }}
            </th>
        </tr>
        </thead>
        <tbody>
        <tr v-if="!rows.length">
            <td
                    class="data-table__empty-message"
                    :colspan="columns.length">
                {{ emptyMessage }}
            </td>
        </tr>
        <tr
                v-else
                v-for="row of rows"
                :key="row[primaryKey]">
            <td
                    v-for="column of columns"
                    :key="column.field"
                    :style="{width: column.width}">
                {{ row[column.field] }}
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
  export default {
    props: {
      primaryKey: {
        type: String,
        required: true
      },
      emptyMessage: {
        type: String,
        default: 'Нет данных'
      },
      columns: {
        type: Array,
        required: true
      },
      rows: {
        type: Array,
        required: true
      }
    }
  };
</script>

<style scoped>
    .data-table {
        width: 100%;
        float: right;
        border-spacing: 0 5px;
        border-collapse: collapse;
        border-radius: 10px;
    }
    .data-table th {
        padding: 5px;
        border-bottom: 1px solid #087d78;
        color: #087d78;
        border-left: 1px solid #087d78;
    }
    .data-table td {
        padding: 5px;
        text-align: center;
        border-bottom: none;
        color: #087d78;
        border-left: 1px solid #087d78;
    }

    .data-table td:first-child {
        border-left: 0;
    }
    .data-table th:first-child {
        border-left: 0;
    }
    td.data-table__empty-message {
        padding: 15px;
        text-align: center;
        color: #087d78;
        border-bottom: none;
    }
</style>
