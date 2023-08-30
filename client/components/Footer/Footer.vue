<script setup lang="ts">
</script>

<template>
  <div class="wrapper">
    <footer class="footer">
      <div class="social-links-block">
        <img src="/footer/footer-logo.png" alt="logo">
        <div class="social-links">
          <NuxtLink to='#' class="social-link">
            <img src="/footer/tg.svg" alt="telegram-icon">
          </NuxtLink>
          <NuxtLink to='#' class="social-link">
            <img src="/footer/fb.svg" alt="facebook-icon">
          </NuxtLink>
          <NuxtLink to='#' class="social-link">
            <img src="/footer/tw.svg" alt="twitter-icon">
          </NuxtLink>
        </div>
        <div class="buttons-footer-block">
          <button class="buttons-block__btn buttons-block__btn-dark-style">
            Register
          </button>

          <button class="buttons-block__btn buttons-block__btn-light-style">
            Sign in
          </button>
        </div>
      </div>
      <div class="links-block">
        <NuxtLink to="#" class="links-block__link">
          Trade
        </NuxtLink>
        <NuxtLink to="#" class="links-block__link">
          P2P
        </NuxtLink>
        <NuxtLink to="#" class="links-block__link">
          Partners
        </NuxtLink>
        <NuxtLink to="#" class="links-block__link">
          Mining
        </NuxtLink>
        <NuxtLink to="#" class="links-block__link">
          Academy
        </NuxtLink>
        <NuxtLink to="#" class="links-block__link">
          Privacy policy
        </NuxtLink>
        <NuxtLink to="#" class="links-block__link">
          Terms of rules
        </NuxtLink>
      </div>
    </footer>
    <p class="copyright">
      Bitlist© All Rights Reserved
    </p>
  </div>
</template>

<style>
  @import url('~/styles/components/Footer.css');
</style>