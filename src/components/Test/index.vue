<template>
  <input type="text" :value="user.name" @keypress="userChange">
</template>

<script>
export default {
  name: 'Test',
  props: {
    user: {Object}
  },
  setup(props,{ emit}) {
    const userChange = event => {
      emit('userChange', event.target.value);
    };

    return {
      userChange
    }
  }
}
</script>

<style>
</style>