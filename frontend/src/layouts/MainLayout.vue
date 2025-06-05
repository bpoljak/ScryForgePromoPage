<template>
  <q-layout view="hHh lpR fFf">
    <!-- Header -->
    <q-header elevated class="bg-primary text-white">
      <q-toolbar class="q-px-md q-gutter-sm">
        <q-toolbar-title class="text-h6">ScryForge</q-toolbar-title>
        <q-space />
        <q-btn
          label="Try it out"
          flat
          no-caps
          class="text-white"
          href="https://scryforge.netlify.app/#/"
          target="_blank"
        />
      </q-toolbar>
    </q-header>

    <!-- Page Content -->
    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-dark text-white q-px-lg q-py-sm">
      <div class="row items-center justify-between">
        <div class="text-caption">© 2025 ScryForge</div>
        <div class="row items-center q-gutter-sm">
          <a
            href="https://www.facebook.com/profile.php?id=61577240033083"
            target="_blank"
            aria-label="Facebook"
          >
            <q-icon name="mdi-facebook" size="20px" class="text-white" />
          </a>
          <a href="https://www.instagram.com/scryforge/" target="_blank" aria-label="Instagram">
            <q-icon name="mdi-instagram" size="20px" class="text-white" />
          </a>
          <a href="https://discord.gg/NvsbH7ny" target="_blank" aria-label="Discord">
            <q-icon name="mdi-discord" size="20px" class="text-white" />
          </a>
          <q-separator vertical dark spaced />
          <a href="/privacy" class="text-white text-caption">PRIVACY</a>
          <a href="/terms" class="text-white text-caption q-ml-sm">TERMS</a>
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script setup>
// Za sada nije potreban dodatni JS
</script>

<style scoped>
a {
  text-decoration: none;
  font-size: 14px;
}
a:hover {
  text-decoration: underline;
}
</style>
