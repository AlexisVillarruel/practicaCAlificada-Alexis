<template>
  <q-input
    v-model="date"
    mask="####-##-##"
    label="Seleccione una fecha"
    type="date"
    outlined
  />
</template>

<script>
export default {
  name: "DatePicker",
  props: ["value"],
  computed: {
    date: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit("input", value);
      },
    },
  },
};
</script>
