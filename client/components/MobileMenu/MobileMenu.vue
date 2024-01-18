<script setup lang="ts">
  defineProps(['mobileMenuActive'])
</script>

<template>
  <transition enter-active-class="animate__animated animate__fadeInLeft" leave-active-class="animate__animated animate__fadeOutRight" mode="out-in">
    <div v-if="mobileMenuActive" class="mobile-menu-wrapper">
      <nav class="search-bar__nav">
        <ul class="search-bar__nav__list-mobile">
          <li class="search-bar__nav__list__item-mobile ">
            <NuxtLink class="search-bar__nav__list__item__link-mobile" to="#">Trade</NuxtLink>
          </li>
          <li class="search-bar__nav__list__item-mobile">
            <NuxtLink class="search-bar__nav__list__item__link-mobile" to="#">P2P</NuxtLink>
          </li>
          <li class="search-bar__nav__list__item-mobile">
            <NuxtLink class="search-bar__nav__list__item__link-mobile" to="#">Partners</NuxtLink>
          </li>
          <li class="search-bar__nav__list__item-mobile">
            <NuxtLink class="search-bar__nav__list__item__link-mobile" to="#">Mining</NuxtLink>
          </li>
          <li class="search-bar__nav__list__item-mobile">
            <NuxtLink class="search-bar__nav__list__item__link-mobile" to="#">Academy</NuxtLink>
          </li>
        </ul>
      </nav>
      <div class="buttons-block-mobile">
        <button class="buttons-block__btn-mobile buttons-block__btn-dark-style">Register</button>
        <button class="buttons-block__btn-mobile buttons-block__btn-light-style">Log In</button>
      </div>
    </div>
  </transition>

</template>

<style>
  @import url('~/styles/components/MobileMenu.css');
  @import url('~/styles/components/Header.css');
</style>