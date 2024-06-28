<template>
  <q-card class="q-mb-md">
    <q-card-section>
      <div class="text-h6">{{ item.title }}</div>
      <div>{{ item.date }}</div>
    </q-card-section>
    <q-card-section>
      <img :src="item.url" alt="APOD Image" class="full-width" />
    </q-card-section>
  </q-card>
</template>

<script>
export default {
  name: "ApodItem",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.full-width {
  width: 100%;
}
</style>
