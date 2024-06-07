<script setup lang="ts">
const { $gsap } = useNuxtApp();

const { data: navigation } = await useAsyncData('navigation', () => fetchContentNavigation());

onMounted(() => {
  $gsap.fromTo('nav', { y: -50, visibility: 'hidden' }, { y: 0, visibility: 'visible', duration: 0.1, transition: "power1.in" })
})
</script>

<template>
  <nav class="invisible">
    <div class="container mx-auto flex items-center py-6">
      <span class="cursor-pointer">
        <img src="/img/pmd-logo-black.svg" alt="Website Logo" class="w-20">
      </span>
      <div class="ml-14">
        <ul class="flex items-center">
          <li :class="[
              'ease-in duration-100 text-lg uppercase font-bold m-0 mr-6 cursor-pointer hover:text-gray-700',
              $route.path === navItem._path ? 'text-gray-900' : 'text-gray-400'
          ]"
              v-for="navItem of navigation">
            <NuxtLink :to="navItem._path">
            {{ navItem.title }}
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style scoped>

</style>
