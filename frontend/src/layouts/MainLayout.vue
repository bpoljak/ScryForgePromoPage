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
      <div class="q-mt-lg text-white text-center q-pt-lg q-pb-md">
        <div class="row justify-center items-center q-gutter-md">
          <a
            href="https://www.facebook.com/profile.php?id=61577240033083"
            target="_blank"
            aria-label="Facebook"
          >
            <q-icon name="mdi-facebook" size="24px" class="text-white" />
          </a>
          <a href="https://www.instagram.com/scryforge/" target="_blank" aria-label="Instagram">
            <q-icon name="mdi-instagram" size="24px" class="text-white" />
          </a>
          <a href="https://discord.gg/NvsbH7ny" target="_blank" aria-label="Discord">
            <q-icon name="mdi-discord" size="24px" class="text-white" />
          </a>
          <q-space />
          <a href="/privacy" class="text-white text-caption">PRIVACY</a>
          <a href="/terms" class="text-white text-caption q-ml-md">TERMS</a>
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script setup>
// no logic needed
</script>

<style scoped></style>
