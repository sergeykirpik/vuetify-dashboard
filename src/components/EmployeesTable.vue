<template>
  <v-data-table
    multi-sort
    :headers="headers"
    :items="employees"
    :items-per-page="5"
    class="elevation-1"
    @click:row="handleRowClick"
  ></v-data-table>
</template>

<script>
export default {
  props: {
    employees: {
      type: Array,
      required: true,
    },
  },
  data: () => ({
    headers: [
      {
        text: "ID",
        align: "start",
        sortable: false,
        value: "id",
      },
      { text: "Name", value: "name" },
      { text: "Title", value: "title" },
      { text: "Salary", value: "salary" },
    ],
  }),
  methods: {
    handleRowClick(rowData) {
      this.$emit("select-employee", rowData);
    },
  },
};
</script>