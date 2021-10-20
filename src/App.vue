<template>
  <Settings :user="user" @handleUser="updateUser" />

  <section class="signature" ref="signature">
    <MailTemplate :name="user.name" :role="user.role" :url="user.url" />
  </section>
  
</template>

<script>
import { reactive } from 'vue';
import MailTemplate from './components/MailTemplate';
import Settings from './components/Settings';

export default {
  name: 'App',
  components: {
    MailTemplate,
    Settings
  },
  setup() {
    const user = reactive({
      name: 'Nombre completo',
      role: 'Pixel Juicer',
      url: 'sidiostedalimones.com'
    });

    const updateUser = data => {
      user.name = data.name;
      user.role = data.role;
      user.url = data.url;
    }



    return {
      user,
      updateUser
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
