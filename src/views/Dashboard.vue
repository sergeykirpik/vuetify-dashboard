<template>
  <div class="px-5">
    <h1>Dashboard</h1>
    <v-data-table
      multi-sort
      :headers="headers"
      :items="employees"
      :items-per-page="5"
      class="elevation-1"
      @click:row="handleRowClick"
    ></v-data-table>
    <v-snackbar v-model="snackbar">
      {{ text }}

      <template v-slot:action="{ attrs }">
        <v-btn color="success" dark v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import employees from "@/data/employees.json";
export default {
  methods: {
    handleRowClick(row) {
      this.text = `${row.name} - ${row.title}`;
      this.snackbar = true;
    },
  },
  data: () => ({
    snackbar: false,
    text: "",
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
    employees,
  }),
};
</script>