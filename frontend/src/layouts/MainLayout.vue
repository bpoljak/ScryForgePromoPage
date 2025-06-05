<template>
  <q-layout view="hHh lpR fFf">

    <!-- Header -->
    <q-header elevated class="bg-grey-10 text-grey-2">
      <q-toolbar class="q-px-md q-gutter-sm">
        <q-toolbar-title class="text-h6 text-weight-bold">ScryForge</q-toolbar-title>
        <q-space />
        <q-btn
          label="Try it out"
          flat
          no-caps
          class="text-grey-2"
          href="https://scryforge.netlify.app/#/"
          target="_blank"
        />
      </q-toolbar>
    </q-header>

    <!-- Page content -->
    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-grey-10 text-grey-4 q-pa-md">
      <div class="row items-center justify-between">
        <div>&copy; 2025 ScryForge</div>
        <div class="row items-center q-gutter-md">
          <q-btn flat dense round size="sm" icon="mdi-facebook" href="https://facebook.com" target="_blank" />
          <q-btn flat dense round size="sm" icon="mdi-instagram" href="https://instagram.com" target="_blank" />
          <q-btn flat dense round size="sm" icon="mdi-discord" href="https://discord.com" target="_blank" />
          <q-btn flat dense label="Privacy" class="text-grey-4" to="/privacy" />
          <q-btn flat dense label="Terms" class="text-grey-4" to="/terms" />
        </div>
      </div>
    </q-footer>

  </q-layout>
</template>

<script setup>
// no logic needed
</script>

<style scoped>
</style>
