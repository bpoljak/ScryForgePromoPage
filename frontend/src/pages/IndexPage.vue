<template>
  <q-page class="bg-dark q-pa-lg">
    <div class="row justify-center">
      <div class="col-12 col-md-10">

        <!-- Hero section -->
        <div class="hero-img-wrapper">
          <img src="~assets/scryforge_intro.jpg" class="hero-img" />
          <div class="absolute hero-overlay animate__animated animate__fadeInUp animate__delay-1s">
            <div class="text-white text-center q-px-md">
              <div class="text-subtitle1 hero-subtitle">Master Your Collection</div>
              <div class="text-h4 text-bold hero-title">Build decks. Track cards. Rule the multiverse.</div>
              <div class="q-mt-md row justify-center q-col-gutter-sm">
                <q-btn label="Start building" color="primary" class="text-black bg-white rounded-borders" to="/register" no-caps />
                <q-btn label="Try it out" flat color="white" class="rounded-borders" href="https://scryforge.netlify.app/#/" target="_blank" no-caps />
              </div>
            </div>
          </div>
        </div>

        <!-- Intro -->
        <div class="text-h5 text-white text-center q-mt-xl q-mb-md animate__animated animate__fadeInUp">
          "ScryForge is your ultimate platform for building, managing and discovering MTG decks – whether you're a casual player or a tournament grinder."
        </div>
        <div class="text-body1 text-grey-4 text-center q-mx-auto animate__animated animate__fadeInUp" style="max-width: 800px">
          Track your collection, organize your decklists, and find new ideas within the MTG community. From Commander to Standard, ScryForge supports every format.
        </div>

        <!-- Benefits -->
        <div class="q-mt-xl animate__animated animate__fadeInUp">
          <div class="text-h5 text-white text-center q-mb-md">Why choose ScryForge?</div>
          <div class="row q-col-gutter-lg justify-center">
            <div class="col-12 col-sm-6 col-md-4" v-for="(benefit, index) in benefits" :key="index">
              <q-card flat bordered class="q-pa-md bg-grey-10 text-white">
                <q-icon :name="benefit.icon" size="lg" class="q-mb-sm" />
                <div class="text-subtitle1">{{ benefit.title }}</div>
                <div class="text-body2 text-grey-4">{{ benefit.desc }}</div>
              </q-card>
            </div>
          </div>
        </div>

        <!-- How it works -->
        <div class="q-mt-xl animate__animated animate__fadeInUp">
          <div class="text-h5 text-white text-center q-mb-md">How it works</div>
          <q-timeline color="primary" layout="dense" class="text-white">
            <q-timeline-entry title="Create your account" subtitle="Sign up in seconds and get started right away" />
            <q-timeline-entry title="Build your deck" subtitle="Add cards, set formats and customize with ease" />
            <q-timeline-entry title="Manage and share" subtitle="Organize collections and share your decks publicly" />
          </q-timeline>
        </div>

        <!-- Problems solved -->
        <div class="q-mt-xl animate__animated animate__fadeInUp">
          <div class="text-h5 text-white text-center q-mb-md">We solve your everyday deckbuilding problems</div>
          <div class="row q-col-gutter-lg justify-center">
            <div class="col-12 col-sm-6 col-md-6" v-for="(issue, index) in problems" :key="index">
              <q-card flat bordered class="q-pa-md bg-grey-9 text-white">
                <div class="text-subtitle1 q-mb-sm">❓ {{ issue.question }}</div>
                <div class="text-body1 text-grey-4">{{ issue.answer }}</div>
              </q-card>
            </div>
          </div>
        </div>

        <!-- Testimonials -->
        <div class="q-mt-xl animate__animated animate__fadeInUp">
          <div class="text-h5 text-white text-center q-mb-md">What players are saying</div>
          <div class="row q-col-gutter-lg justify-center">
            <div class="col-12 col-sm-6 col-md-4" v-for="(review, index) in testimonials" :key="index">
              <q-card flat bordered class="q-pa-md bg-grey-9 text-white">
                <div class="text-subtitle2 q-mb-sm">"{{ review.quote }}"</div>
                <div class="text-caption text-grey-5">- {{ review.name }}</div>
              </q-card>
            </div>
          </div>
        </div>

        <!-- CTA -->
        <div class="q-mt-xl text-center animate__animated animate__fadeInUp">
          <q-separator dark class="q-my-lg" />
          <div class="text-h5 text-white q-mb-sm">Join the Forge today</div>
          <div class="text-body1 text-grey-4 q-mb-md">Free to use. No strings attached.</div>
          <q-btn label="Start for free" color="primary" class="text-black bg-white rounded-borders q-mb-sm" to="/register" no-caps />
          <div class="text-caption text-grey-5">No payment required. Ever.</div>
        </div>

        <!-- FAQ -->
        <div class="q-mt-xl animate__animated animate__fadeInUp">
          <div class="text-h5 text-white text-center q-mb-md">Frequently Asked Questions</div>
          <q-expansion-item
            v-for="(faq, index) in faqs"
            :key="index"
            :label="faq.q"
            :caption="faq.a"
            expand-separator
            class="bg-grey-9 text-white q-mb-sm"
          />
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { useMeta } from 'quasar'

useMeta({
  title: 'ScryForge – MTG Deck Builder & Collection Tracker',
  meta: [
    { name: 'description', content: 'Build and manage your Magic: The Gathering decks and card collection with ScryForge.' },
    { name: 'keywords', content: 'MTG, Magic the Gathering, deck builder, card tracker, collection tool, ScryForge' },
    { property: 'og:title', content: 'ScryForge – Build Your Ultimate MTG Deck' },
    { property: 'og:description', content: 'Track your cards, build decks, and share your MTG builds with the world.' },
    { property: 'og:image', content: 'https://scryforge.netlify.app/banner.png' },
    { property: 'og:url', content: 'https://scryforge.netlify.app/' },
    { property: 'og:type', content: 'website' },
    { property: 'og:site_name', content: 'ScryForge' },
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:title', content: 'ScryForge – MTG Deck Builder' },
    { name: 'twitter:description', content: 'Your new favorite Magic the Gathering deck builder and collection tool.' },
    { name: 'twitter:image', content: 'https://scryforge.netlify.app/banner.png' },
    { name: 'robots', content: 'index, follow' }
  ]
})

const benefits = [
  { icon: 'collections_bookmark', title: 'Deck Management', desc: 'Easily organize all your decks in one place.' },
  { icon: 'inventory', title: 'Collection Tracking', desc: 'Keep track of all cards you own across sets.' },
  { icon: 'public', title: 'Community Decks', desc: 'Discover trending decks and share your own builds.' },
]

const testimonials = [
  { quote: 'ScryForge helped me prep for tournaments faster than ever.', name: 'MTG Arena Grinder' },
  { quote: 'I finally have a clear view of my whole collection.', name: 'Commander Fanatic' },
  { quote: 'Simple, beautiful, and effective.', name: 'Modern Player' },
]

const faqs = [
  { q: 'Is ScryForge free?', a: 'Yes! You can build decks and track your collection completely free.' },
  { q: 'Can I use it on mobile?', a: 'Absolutely. ScryForge works seamlessly on phones and tablets.' },
  { q: 'Does it support Commander format?', a: 'Of course! We support all major MTG formats.' },
]

const problems = [
  { question: 'Do you lose track of your decklists?', answer: 'ScryForge saves and organizes every deck you build.' },
  { question: 'Want to find new card ideas?', answer: 'Browse public decks by format, theme, or popularity.' },
  { question: 'Need to know how many copies you own?', answer: 'Track quantities with our collection manager.' },
  { question: 'Hate exporting to Excel?', answer: 'No spreadsheets needed – everything is managed visually.' },
]
</script>

<style>
@import 'https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css';

.bg-dark {
  background: radial-gradient(circle at top center, #1c1c1c, #101010);
}

.hero-img-wrapper {
  position: relative;
  border-radius: 25px;
  overflow: hidden;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.5);
  max-height: 450px;
  margin-top: -30px;
}

.hero-img {
  width: 100%;
  height: auto;
  display: block;
  object-fit: cover;
  object-position: top;
  border-radius: 25px;
}

.hero-overlay {
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  position: absolute;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  text-align: center;
  padding-top: 180px;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.45), transparent 70%);
}

.hero-title {
  font-size: 2rem;
}

.hero-subtitle {
  font-size: 1rem;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 1.4rem;
  }

  .hero-subtitle {
    font-size: 0.9rem;
  }

  .hero-overlay {
    padding-top: 100px;
  }
}
</style>
