<script setup lang="ts">
  defineEmits(['activemobilemenu'])
</script>

<template>
  <header class="header-wrapper">
    <div class="header">
      <NuxtLink class="logo" to="#">
        <img src="../../assets/img/logo.svg" alt="logo">
      </NuxtLink>
      <div class="search-bar">
        <div class="search-bar__input-wrapper">
          <input class="search-bar__input-wrapper__input" placeholder="Search" type="text">
        </div>
        <nav class="search-bar__nav">
          <ul class="search-bar__nav__list">
            <li class="search-bar__nav__list__item">
              <NuxtLink class="search-bar__nav__list__item__link" to="#">Trade</NuxtLink>
            </li>
            <li class="search-bar__nav__list__item">
              <NuxtLink class="search-bar__nav__list__item__link" to="#">P2P</NuxtLink>
            </li>
            <li class="search-bar__nav__list__item">
              <NuxtLink class="search-bar__nav__list__item__link" to="#">Partners</NuxtLink>
            </li>
            <li class="search-bar__nav__list__item">
              <NuxtLink class="search-bar__nav__list__item__link" to="#">Mining</NuxtLink>
            </li>
            <li class="search-bar__nav__list__item">
              <NuxtLink class="search-bar__nav__list__item__link" to="#">Academy</NuxtLink>
            </li>
          </ul>
        </nav>
      </div>
      <div class="buttons-block">
        <button class="buttons-block__btn buttons-block__btn-dark-style">Register</button>
        <button class="buttons-block__btn buttons-block__btn-light-style">Log In</button>
      </div>
      <div class="burger" @click="$emit('activemobilemenu')">
        <img src="/menu.png" class="burger__icon" alt="menu button">
      </div>
    </div>
  </header>
  <div class="line"></div>
</template>

<style>
  @import url('~/styles/components/Header.css');
</style>
