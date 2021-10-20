<template>
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
</template>

<script>
export default {
  name: 'MailTemplate',
  props: {
    name: String, 
    role: String,
    url: String
  },
}
</script>

<style>
</style>