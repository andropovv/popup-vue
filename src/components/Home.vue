<template>
  <main>
    <section class="info">
      <Info v-if="isShowedInfo" :fieldData="fieldData" />
    </section>
    <section class="start">
      <button class="start-btn" @click="openModal">Начать</button>
    </section>
  </main>
  <Popup
    v-if="isShowedPopup"
    @close="closeModal"
    @change="handleChangeFieldData"
  />
</template>

<script>
import Popup from './Popup.vue';
import Info from './Info.vue';

export default {
  components: { Popup, Info },
  data() {
    return {
      isShowedPopup: false,
      isShowedInfo: false,
      fieldData: {
        Имя: '',
        Фамилия: '',
        Возраст: '',
        'Русский?': '',
        'О себе': '',
      },
    };
  },
  methods: {
    openModal() {
      this.isShowedPopup = true;
    },
    closeModal() {
      this.isShowedPopup = false;
    },
    handleChangeFieldData(data) {
      this.fieldData = data;
      this.isShowedInfo = true;
    },
  },
};
</script>

<style lang="scss">
main {
  max-width: 800px;
  display: flex;
  margin: 0 auto;
  flex-direction: column;

  .info {
    width: 100%;
    min-height: 42vh;
    padding: 10px;
  }
  .start {
    display: flex;
    justify-content: center;
    width: 100%;

    button {
      font-size: 18px;
      cursor: pointer;
    }
  }
}
</style>
