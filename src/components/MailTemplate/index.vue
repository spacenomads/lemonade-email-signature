<template>
  <section class="signature">
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
          {{ user.name }}
        </td>
      </tr>
      <tr>
        <td valign="top" style="font:15px bitter, arial, sans-serif;line-height:22px;mso-line-height-rule:exactly;">
          {{ user.role }}
        </td>
      </tr>
      <tr>
        <td valign="top" style="line-height:20px;mso-line-height-rule:exactly;padding:0 0 40px;mso-padding-alt:0 0 40px;">
          <a href="https://{{ user.url }}" target="_blank" rel="noopener noreferrer" style="text-decoration:none;font:14px bitter, arial, sans-serif;color:#008AFF;">{{ user.url }}</a>
        </td>
      </tr>
    </table>
  </section>
</template>

<script>
import { useStore } from 'vuex';
import { computed } from 'vue';
export default {
  name: 'MailTemplate',
  setup() {
    const store = useStore();

    return {
      user: computed( () => store.state.user ),
    }
  }
}
</script>

<style>
</style>