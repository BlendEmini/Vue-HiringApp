<script setup>
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCards.vue";
import JobListing from "@/components/JobListing.vue";
</script>

<template>
  <Hero title="Test Title" subtitle="Test subtitle" />
  <HomeCards />
  <JobListing :show-button="true" :limit="3" />
</template>
