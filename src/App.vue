<template>
  <form class="form">
    <div class="form__row">
      <label for="signatureName" class="form__label">Nombre</label>
      <input type="text" id="signatureName" name="signatureName" class="form__field" v-model="name">
    </div>

    <div class="form__row">
      <label for="signatureRole" class="form__label">Cargo</label>
      <input type="text" id="signatureRole" name="signatureRole" class="form__field" v-model="role">
    </div>

    <div class="form__row">
      <label for="signatureURL" class="form__label">url</label>
      <input type="text" id="signatureURL" name="signatureURL" class="form__field" v-model="url">
    </div>
  </form>

  <div class="signature" ref="signature">
    <br><br>
    ---
    <br><br>
    <table cellpadding="0" cellspacing="0" border="0">
      <tr>
        <td valign="top" style="padding:0 0 10px;mso-padding-alt:0 0 15px;">
          <img src="https://sidiostedalimones.com/assets/images/mail/lemon.png" width="45" alt="" style="display:block;">
        </td>
      </tr>
      <tr>
        <td valign="top" style="font:bold 17px bitter, arial, sans-serif;line-height:24px;mso-line-height-rule:exactly;">
          {{ name }}
        </td>
      </tr>
      <tr>
        <td valign="top" style="font:15px bitter, arial, sans-serif;line-height:22px;mso-line-height-rule:exactly;">
          {{ role }}
        </td>
      </tr>
      <tr>
        <td valign="top" style="line-height:20px;mso-line-height-rule:exactly;padding:0 0 40px;mso-padding-alt:0 0 40px;">
          <a href="https://{{ url }}" target="_blank" rel="noopener noreferrer" style="text-decoration:none;font:14px bitter, arial, sans-serif;color:#008AFF;">{{ url }}</a>
        </td>
      </tr>

    </table>
  </div>
  <button @click="selectText('.signature')">Selecciona firma</button>
  <p v-if="result">{{ result }}</p>
</template>

<script>
import {ref} from 'vue';

export default {
  name: 'App',
  components: {},
  setup() {
    const name = ref('Nombre completo');
    const role = ref('Pixel Juicer');
    const url = ref('sidiostedalimones.com');
    const result = ref(undefined);

    const signature = ref(null);

    const selectText = () => {
        const range = document.createRange();
        range.selectNode(signature.value);
        window.getSelection().removeAllRanges();
        window.getSelection().addRange(range);
        const successful = document.execCommand('copy');
        
        result.value = successful ? 'Perfecto, está en la saca!' : 'FORK!'

    }

    return {
      name,
      role,
      url,
      selectText,
      signature,
      result
    }
  }
}
</script>

<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
