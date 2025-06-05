<template>
  <q-layout view="hHh lpR fFf">
    <!-- Header -->
    <q-header elevated class="bg-dark text-white">
      <q-toolbar class="q-px-md q-gutter-sm">
        <q-toolbar-title class="text-h6">ScryForge</q-toolbar-title>
        <q-space />
        <q-btn
          label="Try it out"
          href="https://scryforge.netlify.app/#/"
          target="_blank"
          class="try-btn"
          no-caps
          unelevated
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
            <q-icon name="mdi-facebook" size="20px" class="text-white footer-icon" />
          </a>
          <a href="https://www.instagram.com/scryforge/" target="_blank" aria-label="Instagram">
            <q-icon name="mdi-instagram" size="20px" class="text-white footer-icon" />
          </a>
          <a href="https://discord.gg/NvsbH7ny" target="_blank" aria-label="Discord">
            <q-icon name="mdi-discord" size="20px" class="text-white footer-icon" />
          </a>
          <q-separator vertical dark spaced />
          <a href="/privacy" class="text-white text-caption footer-link">PRIVACY</a>
          <a href="/terms" class="text-white text-caption q-ml-sm footer-link">TERMS</a>
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script setup>
// no logic needed
</script>

<style scoped>
.try-btn {
  background-color: rgba(255, 255, 255, 0.08);
  color: white;
  border-radius: 8px;
  padding: 6px 16px;
  transition: all 0.2s ease-in-out;
}
.try-btn:hover {
  background-color: rgba(255, 255, 255, 0.2);
  transform: scale(1.05);
}

.footer-icon:hover {
  opacity: 0.7;
  transform: scale(1.1);
  transition: 0.2s ease-in-out;
}

.footer-link {
  text-decoration: none;
}
.footer-link:hover {
  text-decoration: underline;
}
</style>
