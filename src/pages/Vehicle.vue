<!-- eslint-disable vue/multi-word-component-names -->

<template>
  <h1>Vehicle</h1>
  <div>
    <q-btn label="Nuevo" color="positive" @click="inception = true" />
    <q-dialog v-model="inception">
      <div padding class="bg-white q-pa-xl" style="width: 80%">
        <q-form
          @submit.prevent="procesingForm"
          @reset="reset"
          ref="myForm"
          style="width: 100%"
        >
          <div padding class="q-col-gutter-y-sm">
            <div class="col-12 col-sm-4 col-md-4 col-xxl-3 mb-3">
              <div>
                <q-input
                  outlined
                  label="Matrícula"
                  v-model="plate"
                  pattern="[A-Z]\d{5}"
                  placeholder="******"
                  lazy-rules
                  :rules="[
                    (val) => (val && val.length > 0) || 'Rellene el campo',
                  ]"
                />
              </div>
            </div>
            <div class="col-12 col-sm-4 col-md-4 col-xxl-3 mb-3" id="imp">
              <div>
                <q-select
                  outlined
                  v-model="model"
                  :options="options"
                  label="Modelo"
                  lazy-rules
                  :rules="[
                    (val) => (val && val.length > 0) || 'Rellene el campo',
                  ]"
                />
              </div>
            </div>
            <div class="col-12 col-sm-4 col-md-4 col-xxl-3 mb-3" id="imp">
              <div>
                <q-input
                  outlined
                  label="Capacidad sin equipaje"
                  v-model="capacity_without"
                  placeholder="2"
                  min="2"
                  max="40"
                  lazy-rules
                  :rules="[
                    (val) => (val && val.length > 0) || 'Rellene el campo',
                  ]"
                />
              </div>
            </div>
            <div class="col-12 col-sm-4 col-md-4 col-xxl-3 mb-3" id="imp">
              <div>
                <q-input
                  outlined
                  label="Capacidad con equipaje"
                  v-model="capacity_with"
                  placeholder="2"
                  min="2"
                  max="40"
                  lazy-rules
                  :rules="[
                    (val) => (val && val.length > 0) || 'Rellene el campo',
                  ]"
                />
              </div>
            </div>
            <div class="col-12 col-sm-4 col-md-4 col-xxl-3 mb-3" id="imp">
              <div>
                <q-input
                  outlined
                  label="Capacidad total"
                  v-model="total"
                  placeholder="2"
                  min="2"
                  max="40"
                  lazy-rules
                  :rules="[
                    (val) => (val && val.length > 0) || 'Rellene el campo',
                  ]"
                />
              </div>
            </div>
            <div class="col-12 col-sm-4 col-md-4 col-xxl-3 mb-3" id="imp">
              <div>
                <q-select
                  v-model="selectedYear"
                  outlined
                  :options="optionsyear"
                  label="Select a year"
                />
              </div>
            </div>
            <div class="col-12 col-sm-4 col-md-4 col-xxl-3 mb-3" id="imp">
              <div class="form-floating">
                <q-input
                  v-model="manufacturing"
                  outlined
                  type="textarea"
                  label="Modo de fabricación"
                  rows="3"
                  maxlength="200"
                  lazy-rules
                  :rules="[
                    (val) => (val && val.length > 0) || 'Rellene el campo',
                  ]"
                />
              </div>
            </div>
          </div>
          <div>
            <q-btn
              color="primary"
              label="Aceptar"
              class="q-ml-sm"
              type="submit"
            />
            <q-btn
              color="primary"
              label="Cancelar"
              class="q-ml-sm"
              type="reset"
            />
          </div>
        </q-form>
      </div>
    </q-dialog>
  </div>
  <pintar-vehicles :vehicles="vehicles" />
</template>

<script>
import { ref, onMounted } from "vue";
import PintarVehicles from "src/components/PintarVehicles.vue";

export default {
  components: { PintarVehicles },
  setup() {
    // Variables reactivas
    const optionsyear = ref([]);
    const plate = ref("");
    const capacity_without = ref("");
    const capacity_with = ref("");
    const total = ref("");
    const manufacturing = ref("");
    const model = ref(null);
    const selectedYear = ref(null);
    const myForm = ref(null);

    //Arreglo de vehiculos
    const vehicles = ref([]);

    const generateYears = () => {
      const currentYear = new Date().getFullYear();
      for (let year = 1900; year <= currentYear; year++) {
        optionsyear.value.push(year);
      }
    };
    const procesingForm = () => {
      console.log("me diste click");
      myForm.value.resetValidation();
      //luego se procesa el formulario
      vehicles.value = [
        ...vehicles.value,
        {
          plate: plate.value,
          model: model.value,
          capacity_without: capacity_without.value,
          capacity_with: capacity_with.value,
          total: total.value,
          year: selectedYear.value,
          manufacturing: manufacturing.value,
        },
      ];
      //restablece los valores del formulario
      reset();
    };
    const reset = () => {
      plate.value = null;
      capacity_without.value = null;
      capacity_with.value = null;
      total.value = null;
      manufacturing.value = null;
      model.value = null;
      selectedYear.value = null;
    };

    onMounted(generateYears);

    return {
      plate,
      capacity_without,
      capacity_with,
      total,
      manufacturing,
      model,
      selectedYear,
      optionsyear,
      myForm,
      inception: ref(false),
      options: ["Mercedez", "Audi", "Lada", "Mazda", "Peugot"],
      vehicles,
      procesingForm,
      reset,
      // reset() {
      //   plate.value = null;
      //   capacity_without.value = null;
      //   capacity_with.value = null;
      //   total.value = null;
      //   manufacturing.value = null;
      //   model.value = null;
      //   selectedYear.value = null;
      // },
    };
  },
};
</script>
