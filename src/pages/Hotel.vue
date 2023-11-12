<!-- eslint-disable vue/multi-word-component-names -->

<template>
  <h1>Hotel</h1>
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
                  label="Nombre"
                  v-model="name"
                  pattern="[A-Z]\[a-z]"
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
                  label="Cadena"
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
                  v-model="province"
                  :options="provinces"
                  label="Provincia"
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
                  label="Categoría"
                  v-model="category"
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
                  label="Teléfono"
                  v-model="phone"
                  mask="(7) ### - ####"
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
                  label="Email"
                  v-model="email"
                  type="email"
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
                  label="Número de habitaciones"
                  v-model="rooms"
                  placeholder="10"
                  min="10"
                  max="300"
                  lazy-rules
                  :rules="[
                    (val) => (val && val.length > 0) || 'Rellene el campo',
                  ]"
                />
              </div>
            </div>
            <div class="col-12 col-sm-4 col-md-4 col-xxl-3 mb-3" id="imp">
              <div>
                <!-- Me quede por aqui -->
                <q-input
                  outlined
                  label="Número de pisos"
                  v-model="capacity_with"
                  placeholder="1"
                  min="1"
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
</template>

<script>
import { ref, onMounted } from "vue";
import PintarVehicles from "src/components/PintarVehicles.vue";

export default {
  // components: { PintarVehicles },
  setup() {
    // Variables reactivas
    const optionsyear = ref([]);
    const name = ref("");
    const province = ref(null);
    const category = ref("");
    const phone = ref("");
    const email = ref("");
    const rooms = ref("");
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
          name: name.value,
          model: model.value,
          category: category.value,
          phone: phone.value,
          email: email.value,
          rooms: rooms.value,
          year: selectedYear.value,
          manufacturing: manufacturing.value,
        },
      ];
      //restablece los valores del formulario
      reset();
    };
    const reset = () => {
      name.value = null;
      category.value = null;
      phone.value = null;
      email.value = null;
      rooms.value = null;
      manufacturing.value = null;
      model.value = null;
      selectedYear.value = null;
    };

    onMounted(generateYears);

    return {
      name,
      model,
      category,
      phone,
      email,
      rooms,
      manufacturing,
      province,
      selectedYear,
      optionsyear,
      myForm,
      inception: ref(false),
      options: ["Melia", "Iberostar", "GranCaribe", "Royalton", "Barcelo"],
      provinces: [
        "Pinar del Río",
        "Artemisa",
        "La Habana",
        "Mayabeque",
        "Matanzas",
        "Cienfuegos",
        "Villa Clara",
        "Sancti Spíritus",
        "Ciego de Ávila",
        "Camagüey",
        "Las Tunas",
        "Granma",
        "Holguín",
        "Santiago de Cuba",
        "Guantánamo",
        " Isla de la Juventud",
      ],
      vehicles,
      procesingForm,
      reset,
    };
  },
};
</script>
