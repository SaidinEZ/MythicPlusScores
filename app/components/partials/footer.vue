<template>
  <footer class="footer -mx-4 md:mx-0">
    <div class="container mx-auto pb-6 flex justify-center text-white">
      <div class="flex flex-col text-center items-center text-white">
          <svg width="41px" height="39px" viewBox="0 0 41 39" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
            <g id="Page-1" stroke="none" stroke-width="1" fill="#0b3765" fill-rule="evenodd">
              <path d="M11.6322341,0.621339181 C-0.98156407,7.0360394 -3.15905398,23.3580119 4.23659007,33.149238 C11.6322341,42.9404641 19.5139375,38.037723 23.8409829,33.149238 C26.9029455,29.3705858 41,42.6044308 41,33.149238 C41,23.6940452 37.9646378,13.4507395 28.1680282,7.0360394 C18.3714187,0.621339181 14.9894036,-1.08593688 11.6322341,0.621339181 Z" id="Path" fill="#ffffff" fill-rule="nonzero"></path>
            </g>
          </svg>
          <p class="text-bluise mt-2">
            Enkazin
          </p>
       </div>
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
  background-color: #fff;
}
</style>
