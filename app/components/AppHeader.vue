<script setup lang="ts">
const nuxtApp = useNuxtApp();
const { activeHeadings, updateHeadings } = useScrollspy();

const items = computed(() => [
  {
    label: "Home",
    to: "#home",
    active:
      activeHeadings.value.includes("services") &&
      !activeHeadings.value.includes("projects"),
  },
  {
    label: "Services",
    to: "#services",
    active: activeHeadings.value.includes("services"),
  },
  {
    label: "Projects",
    to: "#projects",
    active:
      activeHeadings.value.includes("services") &&
      !activeHeadings.value.includes("projects"),
  },
]);

nuxtApp.hooks.hookOnce("page:finish", () => {
  updateHeadings(
    [
      document.querySelector("#home"),
      document.querySelector("#services"),
      document.querySelector("#projects"),
    ].filter(Boolean) as Element[]
  );
});
</script>

<template>
  <UHeader>
    <template #left>
      <NuxtLink to="/">
        <AppLogo class="w-auto h-6 shrink-0" />
      </NuxtLink>
    </template>

    <template #right>
      <UNavigationMenu :items="items" variant="link" class="hidden lg:block" />

      <UButton
        label="Get in contact"
        variant="subtle"
        class="hidden lg:block"
        to="#contact"
      />

      <UColorModeButton />
    </template>

    <template #body>
      <UNavigationMenu :items="items" orientation="vertical" class="-mx-2.5" />
      <UButton class="mt-4" label="Get in contact" variant="subtle" block />
    </template>
  </UHeader>
</template>
