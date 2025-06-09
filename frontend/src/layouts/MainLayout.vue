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
    <q-dialog v-model="showCookiePopup" persistent position="bottom">
      <q-card class="cookie-popup q-pa-md text-white">
        <div class="row items-center justify-between q-gutter-md">
          <div class="col text-body2">
            This site uses cookies to improve your experience. Accept or reject?
          </div>
          <div class="row q-gutter-sm">
            <q-btn flat label="Reject" color="white" @click="rejectCookies" class="cookie-btn" />
            <q-btn
              unelevated
              label="Accept"
              color="primary"
              @click="acceptCookies"
              class="cookie-btn"
            />
          </div>
        </div>
      </q-card>
    </q-dialog>
  </q-layout>
</template>

<script setup>
/* global gtag */

import { ref, onMounted } from 'vue'

const showCookiePopup = ref(false)
const GA_ID = 'G-W7C5EHH329'

onMounted(() => {
  const c = localStorage.getItem('cookiesChoice')
  if (c === 'accepted') loadGoogleAnalytics()
  else if (!c) showCookiePopup.value = true
})

function acceptCookies() {
  localStorage.setItem('cookiesChoice', 'accepted')
  showCookiePopup.value = false
  window['ga-disable-G-W7C5EHH329'] = false
  console.log('[TEST] acceptCookies triggered')
  loadGoogleAnalytics()
}

function rejectCookies() {
  localStorage.setItem('cookiesChoice', 'rejected')
  showCookiePopup.value = false
  window['ga-disable-G-W7C5EHH329'] = true
  window.gtag = function () {}
  document.cookie = '_ga=; Max-Age=0; path=/'
  document.cookie = '_gid=; Max-Age=0; path=/'

  // Remove GA scripts again in case injected
  document.querySelectorAll('script[src*="googletagmanager.com"]').forEach((s) => s.remove())
}

function loadGoogleAnalytics() {
  if (window.gtagLoaded || window['ga-disable-G-W7C5EHH329']) return
  window.gtagLoaded = true

  const scriptTag = document.createElement('script')
  scriptTag.setAttribute('async', '')
  scriptTag.src = `https://www.googletagmanager.com/gtag/js?id=${GA_ID}`
  scriptTag.onerror = () => {
    console.error('❌ GA script failed to load')
  }
  document.head.appendChild(scriptTag)

  scriptTag.onload = () => {
    console.log('✅ GA script loaded after accept')
    window.dataLayer = window.dataLayer || []
    window.gtag = function () {
      window.dataLayer.push(arguments)
    }
    gtag('js', new Date())
    gtag('config', GA_ID)
  }
}
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

.cookie-popup {
  background: rgba(40, 40, 40, 0.95);
  border-radius: 12px;
  max-width: 700px;
  width: 90%;
  margin: auto;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.4);
}

.cookie-btn {
  border-radius: 8px;
  padding: 6px 16px;
}
</style>
