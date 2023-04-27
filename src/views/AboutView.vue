<script setup>
import TimelineHistory from '@/components/TimelineHistory.vue'
</script>

<template>
  <div class="about">
    <h1>Timeline of History</h1>
    <TimelineHistory />
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
