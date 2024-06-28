<template>
  <q-page class="q-pa-md">
    <q-form @submit.prevent="fetchApodData">
      <div class="q-mb-md">
        <DatePicker v-model="startDate" label="Fecha Inicio" />
      </div>
      <div class="q-mb-md">
        <DatePicker v-model="endDate" label="Fecha Fin" />
      </div>
      <q-btn type="submit" label="Consultar" color="primary" />
    </q-form>

    <q-space />

    <ApodList v-if="apodData.length" :apodData="apodData" />
  </q-page>
</template>

<script>
import DatePicker from "components/DatePicker.vue";
import ApodList from "components/ApodList.vue";
import axios from "axios";

export default {
  name: "NasaApod",
  components: {
    DatePicker,
    ApodList,
  },
  data() {
    return {
      startDate: "",
      endDate: "",
      apodData: [],
    };
  },
  methods: {
    async fetchApodData() {
      const apiKey = "16nGRIogYbQzfjEwstOvz02dKzmT7yXnPclzMO32";
      const url = `https://api.nasa.gov/planetary/apod?api_key=${apiKey}&start_date=${this.startDate}&end_date=${this.endDate}`;
      try {
        const response = await axios.get(url);
        this.apodData = response.data;
      } catch (error) {
        console.error("Error fetching APOD data:", error);
      }
    },
  },
};
</script>
