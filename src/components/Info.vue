<template>
  <p v-for="field in Object.entries(fieldData)">
    {{ field[0] }}:
    {{ typeof field[1] == 'boolean' ? (field[1] ? 'Да' : 'Нет') : field[1] }}
  </p>
  <p>{{ JSON.stringify(fieldData) }}</p>
</template>

<script>
export default {
  props: {
    fieldData: Object,
  },
};
</script>
<style scoped lang="scss"></style>
