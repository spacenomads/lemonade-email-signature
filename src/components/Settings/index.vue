<template>
  <section class="app__settings">
    <form class="form">
      <div class="form__row">
        <label for="signatureName" class="form__label">Nombre</label>
        <input type="text" id="signatureName" name="signatureName" class="form__field" v-model="user.name">
      </div>
      <div class="form__row">
        <label for="signatureRole" class="form__label">Cargo</label>
        <input type="text" id="signatureRole" name="signatureRole" class="form__field" v-model="user.role">
      </div>
      <div class="form__row">
        <label for="signatureURL" class="form__label">url</label>
        <input type="text" id="signatureURL" name="signatureURL" class="form__field" v-model="user.url">
      </div>

      <div class="form__row">
        <button type="button" @click="selectText()">Al portapapeles!</button>
      </div>
    </form>
    <div class="app__notification" :class="getNotificationStatus">
      <p>{{ result }}</p>
    </div>
  </section>
</template>

<script>
import { ref, computed } from 'vue';
import { useStore } from 'vuex';

const SIGNATURE_SELECTOR = '.signature';
const NOTIFICATION_DELAY = 1000;
const NOTIFICATION_OK = '🤟 Perfecto, está en la saca!';
const NOTIFICATION_KO = '💩 FORK!';

export default {
  name: 'Settings',
  setup() {
    const store = useStore();
    const notification =  ref(false);
    const result = ref(undefined);

    const selectText = () => {
      const signature = document.querySelector(SIGNATURE_SELECTOR)
      const range = document.createRange();
      range.selectNode(signature);
      window.getSelection().removeAllRanges();
      window.getSelection().addRange(range);
      const successful = document.execCommand('copy');
      result.value = successful ? NOTIFICATION_OK : NOTIFICATION_KO;
      notification.value = true;

      setTimeout(()=>{
        notification.value = false;
      }, NOTIFICATION_DELAY);
    };

    const getNotificationStatus = computed(() => {
      return notification.value ? 'app__notification--visible' : null;
    });


    return {
      user: computed( ()=>store.state.user ),
      selectText,
      result,
      notification,
      getNotificationStatus,
    }
  }
}
</script>

<style>
  .app__notification {
    position: fixed;
    right: 1em;
    top: 1em;
    transform: translateY(-200%);
    transition: transform ease .5s;
  }
  .app__notification--visible {
    transform: translateY(0);
  }
</style>