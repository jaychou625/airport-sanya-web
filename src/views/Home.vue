<template>
  <div class="home">
    <Header />
    <div class="content">
      <LeftNav class="leftNav" />
    </div>
  </div>
</template>

<style lang="stylus">
  .home
    width 1440px
    margin 0 auto
  .content:after
    content:'';
    display block;
    clear:both;
  .leftNav
    float left
</style>


<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Header from '@/components/public/header/header.vue'; // @ is an alias to /src
import LeftNav from '@/components/public/navigate/leftNav.vue'; // @ is an alias to /src


@Component({
  components: {
    Header,
    LeftNav,
  },
})
export default class Home extends Vue {}
</script>
