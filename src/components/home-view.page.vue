<template>
  <div class="home-view">
    <div class="content-wrapper">
      <main class="main-content">
        <FormTutorialComponent/>
      </main>
    </div>
  </div>
</template>

<script setup>

import FormTutorialComponent from "@/components/form-tutorial.component.vue";

</script>

<style scoped>

.home-view {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

.content-wrapper {
  display: flex;
  flex: 1;
}

.main-content {
  flex: 1;
  padding: 1rem;
}
</style>
