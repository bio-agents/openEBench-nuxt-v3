<template>
  <div class="agent h-100">
    <BreadcrumbsBar :breadcrumbs-array="routeArray" />
    <div class="container">
      <iframe :src="iframeSRC" width="100%" height="100%" frameborder="0">
      </iframe>
    </div>
  </div>
</template>

<script setup lang="ts">
import BreadcrumbsBar from "@/components/Common/BreadcrumbsBar.vue";

const route = useRoute();
const runtimeConfig = useRuntimeConfig();
const hostname = runtimeConfig.public.OEB_LEGACY_ANGULAR_URI;
const query = route.query.search ? route.query.search : "";
const iframeSRC = `${hostname}agent?search=${query}`;

definePageMeta({
  layout: "embed-iframe-full-width",
});

const routeArray: Array = [{ label: "Agent", isActualRoute: true }];
</script>

<style scoped lang="scss">
.agent {
  flex: 1 1 auto;
  backface-visibility: hidden;

  min-height: 100vh;
  max-width: 100%;
  position: relative;
  iframe {
    height: 100vh;
  }
}
</style>
