<template>
  <router-view></router-view>
</template>

<script>
import auth from './components/auth.vue';

export default {
  name: 'app',
  components: {
    'auth': auth,
  },
  data () {
    return {
    }
  }
}
</script>

<style lang="scss">
</style>
