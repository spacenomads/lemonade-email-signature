<template>
  <Settings />
  <MailTemplate />
</template>

<script>
import MailTemplate from './components/MailTemplate';
import Settings from './components/Settings';

export default {
  name: 'App',
  components: {
    MailTemplate,
    Settings
  },
}
</script>

<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
