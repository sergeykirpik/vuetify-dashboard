<template>
  <v-container fluid>
    <h1>Dashboard</h1>

    <!-- Sales Graphs -->
    <v-row>
      <v-col v-for="sale in sales" :key="`${sale.title}`" cols="12" md="4">
        <SalesGraph :sale="sale" />
      </v-col>
    </v-row>

    <!-- Statistic Cards -->
    <v-row>
      <v-col
        v-for="statistic in statistics"
        :key="`${statistic.title}`"
        cols="12"
        md="6"
        lg="3"
      >
        <StatisticCard :statistic="statistic" />
      </v-col>
    </v-row>

    <!-- Employees and Timeline -->
    <v-row>
      <v-col cols="12" md="8">
        <h3>Employees Table</h3>
        <EmployeesTable
          :employees="employees"
          @select-employee="selectEmployee"
        />
      </v-col>
      <v-col cols="12" md="4">
        <h3>Event Timeline</h3>
        <EventTimeLine :timeline="timeline" />
      </v-col>
    </v-row>

    <!-- Snackbar -->
    <v-snackbar v-model="snackbar" :left="$vuetify.breakpoint.lgAndUp">
      {{ text }}

      <template v-slot:action="{ attrs }">
        <v-btn color="success" dark v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </v-container>
</template>

<script>
import employees from "@/data/employees.json";
import statistics from "@/data/statistics.json";
import sales from "@/data/sales.json";
import timeline from "@/data/timeline.json";
import SalesGraph from "@/components/SalesGraph.vue";
import StatisticCard from "@/components/StatisticCard.vue";
import EmployeesTable from "@/components/EmployeesTable.vue";
import EventTimeLine from "@/components/EventTimeLine.vue";
export default {
  components: { EmployeesTable, StatisticCard, SalesGraph, EventTimeLine },
  methods: {
    selectEmployee(row) {
      this.text = `${row.name} - ${row.title}`;
      this.snackbar = true;
    },
  },
  data: () => ({
    snackbar: false,
    text: "",
    employees,
    statistics,
    sales,
    timeline,
  }),
};
</script>