<template>
  <div class="container">
    <div class="back" @click="closePopup"></div>
    <div class="popup">
      <div v-for="(field, i) in fields" class="field">
        <label :htmlFor="'field' + i">{{ field.name }}</label>
        <input
          v-model="fieldData[field.name]"
          v-if="field.type != 'textarea'"
          :id="'field' + i"
          :type="field.type"
        />
        <textarea v-else :id="field.name" v-model="fieldData[field.name]" />
      </div>
      <button @click="submit">Отправить</button>
    </div>
  </div>
</template>
<script>
export default {
  emits: ['close', 'change'],
  methods: {
    closePopup() {
      this.$emit('close');
    },
    submit() {
      this.$emit('change', this.fieldData);
      this.$emit('close');
    },
  },
  data() {
    return {
      fields: [
        { name: 'Имя', type: 'text' },
        { name: 'Фамилия', type: 'text' },
        { name: 'Возраст', type: 'number' },
        { name: 'Русский?', type: 'checkbox' },
        { name: 'О себе', type: 'textarea' },
      ],
      fieldData: {
        Имя: '',
        Фамилия: '',
        Возраст: null,
        'Русский?': false,
        'О себе': '',
      },
    };
  },
};
</script>

<style scoped lang="scss">
.container {
  position: absolute;
  left: 0;
  min-width: 100%;
  top: 0;
  min-height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;

  .back {
    min-width: 100%;
    position: absolute;
    min-height: 100%;
    background-color: black;
    opacity: 0.5;
  }
  .popup {
    max-width: 500px;
    background-color: white;
    border-radius: 5px;
    position: absolute;
    padding: 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;

    .field {
      display: flex;
      gap: 10px;
      justify-content: space-between;
    }
    @media (max-width: 480px) {
      .field {
        flex-direction: column;
        align-items: start;
      }
    }
  }
}
</style>
