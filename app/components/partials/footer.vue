<template>
  <footer class="footer -mx-4 md:mx-0">
    <div class="container mx-auto pb-6 flex justify-center text-white">
      <div>
          <img :src="logo" alt="Logo" class="fill-current" />
      </div>
      <p>
        Enkazin
      </p>
    </div>
  </footer>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';

@Component
export default class Footer extends Vue {}
</script>

<style lang="scss">
.footer {
  background-color: $bluise;
}
</style>
