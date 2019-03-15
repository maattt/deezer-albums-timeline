<template>
  <div id="list">
    <ul>
      <li v-for="album in albums" class="album">
        <!-- <strong>{{album.title}}, {{album.release_date.substring(0,4)}}</strong> -->
        <a href="#"><img v-bind:src="album.cover_medium" class="cover" /></a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      albums: []
    }
  },
  created() {
    var vueObject = this;
    DZ.api('/user/me/albums', function(response) {
      if (typeof response.error !== 'undefined') {
        vueObject.$router.push('/');
      }
      vueObject.albums = response.data;
    });
  }
}
</script>

<style lang="scss">
  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
    text-align: center;
  }

  .album {
    display: inline-block;

    a {
      display: block;
      padding: 3px;
      &:hover {
      }
    }
  }
</style>
