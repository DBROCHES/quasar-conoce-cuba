<template>
  <q-table
    title="Vehículos"
    class="q-mt-md"
    no-data-label="Sin vehículos para mostrar"
    :columns="columns"
    :rows="vehicles"
  ></q-table>
</template>
<script>
const columns = [
  {
    name: "plate",
    label: "Matrícula",
    alingn: "left",
    field: "plate",
    sortable: true,
  },
  {
    name: "model",
    label: "Modelo",
    alingn: "left",
    field: "model",
    sortable: true,
  },
  {
    name: "capacity_without",
    label: "Capacidad sin equipaje",
    alingn: "left",
    field: "capacity_without",
    sortable: true,
  },
  {
    name: "capacity_with",
    label: "Capacidad con equipaje",
    alingn: "left",
    field: "capacity_with",
    sortable: true,
  },
  {
    name: "total",
    label: "Capacidad total",
    alingn: "left",
    field: "total",
    sortable: true,
  },
  {
    name: "year",
    label: "Año de fabricación",
    alingn: "left",
    field: "year",
    sortable: true,
  },
  {
    name: "manufacturing",
    label: "Modo de fabricación",
    alingn: "left",
    field: "manufacturing",
    sortable: true,
  },
];

const rows = [
  {
    plate: "A12365",
    model: "Audi",
    capacity_without: "2",
    capacity_with: "2",
    total: "2",
    year: "2000",
    manufacturing: "industrial",
  },
];

export default {
  props: {
    vehicles: Array,
  },
  setup() {
    return {
      columns,
      rows,
    };
  },
};
</script>
