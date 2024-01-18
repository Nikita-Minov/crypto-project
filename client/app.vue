<script setup lang="ts">

  const mobileMenuActive = ref(false);

  const toggleMobileMenuActive = () => {
    if(document.getElementsByTagName('body')[0].style.overflowY == 'hidden') {
      document.getElementsByTagName('body')[0].style.overflowY = 'scroll';
    } else {
      document.getElementsByTagName('body')[0].style.overflowY = 'hidden';
    }
    mobileMenuActive.value = !mobileMenuActive.value;
  }
</script>

<template>
  <MobileMenu :mobile-menu-active="mobileMenuActive"/>
  <Header @activemobilemenu="toggleMobileMenuActive"/>
  <NuxtLayout>
    <NuxtPage/>
  </NuxtLayout>
  <Footer/>
</template>

<style>
  @import url('~/styles/main.css');
</style>
