<template>
  <div id="auth">
    Auth
  </div>
</template>

<script>
export default {
  data () {
    return {
    }
  },
  created() {
    var vueObject = this;
    DZ.login(function(response) {
      if (response.authResponse) {
        localStorage.accessToken = response.authResponse.accessToken;
        vueObject.$router.push('/list');
      } else {
        console.log('User cancelled login or did not fully authorize.');
      }
    }, {perms: 'basic_access,email'});
  }
}
</script>

<style lang="scss">
</style>
