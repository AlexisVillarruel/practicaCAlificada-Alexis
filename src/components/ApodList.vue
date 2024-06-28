<template>
  <div>
    <q-table
      v-if="apodData.length"
      :rows="apodData"
      :columns="columns"
      row-key="date"
    />

    <q-space />

    <ApodItem v-for="item in apodData" :key="item.date" :item="item" />
  </div>
</template>

<script>
import ApodItem from "components/ApodItem.vue";

export default {
  name: "ApodList",
  components: {
    ApodItem,
  },
  props: {
    apodData: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      columns: [
        {
          name: "date",
          required: true,
          label: "Fecha",
          align: "left",
          field: "date",
        },
        {
          name: "title",
          required: true,
          label: "Título",
          align: "left",
          field: "title",
        },
      ],
    };
  },
};
</script>
