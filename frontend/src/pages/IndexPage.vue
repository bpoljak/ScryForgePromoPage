<template>
  <q-page class="bg-dark q-pa-lg">
    <div class="row justify-center">
      <div class="col-12 col-md-10">
        <!-- Hero section -->
        <div class="hero-img-wrapper">
          <img src="~assets/page_art2.png" class="hero-img" />
          <div class="absolute hero-overlay animate__animated animate__fadeInUp animate__delay-1s">
            <div class="text-white text-center q-px-md">
              <div class="text-h4 text-bold hero-logo">ScryForge</div>
              <div class="text-subtitle1 hero-subtitle">Master Your Collection</div>
              <div class="text-h4 text-bold hero-title">
                Build decks. Track cards. Rule the multiverse.
              </div>
              <div class="q-mt-md row justify-center q-col-gutter-sm">
                <q-btn
                  label="Start building"
                  color="primary"
                  class="text-black bg-white rounded-borders hero_btn"
                  to="/register"
                  no-caps
                />
                <q-btn
                  label="Try it out"
                  flat
                  color="white"
                  class="rounded-borders hero_btn"
                  href="https://scryforge.netlify.app/#/"
                  target="_blank"
                  no-caps
                />
              </div>
            </div>
          </div>
        </div>

        <!-- Intro -->
        <div
          class="text-h5 text-white text-center q-mt-xl q-mb-md animate__animated animate__fadeInUp"
        >
          "ScryForge is your ultimate platform for building, managing and discovering MTG decks –
          whether you're a casual player or a tournament grinder."
        </div>
        <div
          class="text-body1 text-grey-4 text-center q-mx-auto animate__animated animate__fadeInUp"
          style="max-width: 800px"
        >
          Track your collection, organize your decklists, and find new ideas within the MTG
          community. From Commander to Standard, ScryForge supports every format.
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
            <q-timeline-entry
              title="Create your account"
              subtitle="Sign up in seconds and get started right away"
            />
            <q-timeline-entry
              title="Build your deck"
              subtitle="Add cards, set formats and customize with ease"
            />
            <q-timeline-entry
              title="Manage and share"
              subtitle="Organize collections and share your decks publicly"
            />
          </q-timeline>
        </div>

        <!-- Problems solved -->
        <div class="q-mt-xl animate__animated animate__fadeInUp">
          <div class="text-h5 text-white text-center q-mb-md">
            We solve your everyday deckbuilding problems
          </div>
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
          <div class="row q-col-gutter-lg justify-center items-stretch">
            <div
              class="col-12 col-sm-6 col-md-4"
              v-for="(review, index) in testimonials"
              :key="index"
            >
              <q-card flat bordered class="q-pa-md bg-grey-9 text-white testimonial-card">
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
          <q-btn
            label="Start for free"
            color="primary"
            class="text-black bg-white rounded-borders q-mb-sm"
            href="https://scryforgepromo.netlify.app"
            target="_blank"
            no-caps
          />
          <div class="text-caption text-grey-5">No payment required. Ever.</div>
        </div>

        <!-- FAQ -->
        <div class="q-mt-xl animate__animated animate__fadeInUp">
          <div class="text-h5 text-white text-center q-mb-md">Frequently Asked Questions</div>
          <q-expansion-item
            v-for="(faq, index) in faqs"
            :key="index"
            expand-separator
            switch-toggle-side
            class="bg-grey-9 text-white q-mb-sm faq-item"
            expand-icon="keyboard_arrow_down"
            expanded-icon="keyboard_arrow_up"
          >
            <template #header>
              <div class="row items-center justify-between q-px-md q-py-sm full-width">
                <div class="text-subtitle1 text-weight-bold">
                  {{ faq.q }}
                </div>
              </div>
            </template>
            <div class="q-px-md q-pb-sm text-grey-4">
              {{ faq.a }}
            </div>
          </q-expansion-item>
        </div>

        <!-- Contact -->
        <div class="q-mt-xl animate__animated animate__fadeInUp">
          <div class="text-h5 text-white text-center q-mb-md">Have a question or suggestion?</div>
          <div class="text-body1 text-grey-4 text-center q-mb-lg">
            Send us a message and we’ll get back to you!
          </div>
          <q-form @submit.prevent="sendEmail" class="q-gutter-md" ref="formRef">
            <div class="row q-col-gutter-md">
              <div class="col-12 col-md-6">
                <q-input
                  v-model="form.name"
                  label="Your Name"
                  dense
                  outlined
                  class="bg-grey-9 text-white"
                  :rules="[(val) => !!val || 'Name is required']"
                />
              </div>
              <div class="col-12 col-md-6">
                <q-input
                  v-model="form.email"
                  label="Your Email"
                  type="email"
                  dense
                  outlined
                  class="bg-grey-9 text-white"
                  :rules="[(val) => !!val || 'Email is required']"
                />
              </div>
              <div class="col-12">
                <q-input
                  v-model="form.message"
                  type="textarea"
                  label="Your Message"
                  outlined
                  class="bg-grey-9 text-white"
                  autogrow
                  :rules="[(val) => !!val || 'Message is required']"
                />
              </div>
              <div class="col-12 text-center">
                <q-btn label="Send" type="submit" color="primary" class="text-black bg-white" />
              </div>
            </div>
          </q-form>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref, getCurrentInstance } from 'vue'
import emailjs from '@emailjs/browser'
import { useMeta } from 'quasar'

const { proxy } = getCurrentInstance()
const $q = proxy.$q

useMeta({
  title: 'ScryForge – MTG Deck Builder & Collection Tracker',
  meta: [
    {
      name: 'description',
      content:
        'Build and manage your Magic: The Gathering decks and card collection with ScryForge.',
    },
    {
      name: 'keywords',
      content: 'MTG, Magic the Gathering, deck builder, card tracker, collection tool, ScryForge',
    },
    { property: 'og:title', content: 'ScryForge – Build Your Ultimate MTG Deck' },
    {
      property: 'og:description',
      content: 'Track your cards, build decks, and share your MTG builds with the world.',
    },
    { property: 'og:image', content: 'https://scryforge.netlify.app/banner.png' },
    { property: 'og:url', content: 'https://scryforge.netlify.app/' },
    { property: 'og:type', content: 'website' },
    { property: 'og:site_name', content: 'ScryForge' },
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:title', content: 'ScryForge – MTG Deck Builder' },
    {
      name: 'twitter:description',
      content: 'Your new favorite Magic the Gathering deck builder and collection tool.',
    },
    { name: 'twitter:image', content: 'https://scryforge.netlify.app/banner.png' },
    { name: 'robots', content: 'index, follow' },
  ],
})

const formRef = ref(null)
const form = ref({
  name: '',
  email: '',
  message: '',
})

function sendEmail() {
  const serviceId = import.meta.env.VITE_EMAILJS_SERVICE_ID
  const templateId = import.meta.env.VITE_EMAILJS_TEMPLATE_ID
  const userId = import.meta.env.VITE_EMAILJS_USER_ID

  if (!serviceId || !templateId || !userId) {
    $q.notify({
      type: 'negative',
      message: 'Missing EmailJS environment variables.',
    })
    return
  }

  const templateParams = {
    from_name: form.value.name,
    from_email: form.value.email,
    message: form.value.message,
    email: form.value.email, // Ovo je za "To Email" polje u EmailJS templateu
  }

  emailjs
    .send(serviceId, templateId, templateParams, userId)
    .then(() => {
      $q.notify({
        type: 'positive',
        message: 'Message sent successfully!',
      })
      formRef.value.reset()
    })
    .catch((error) => {
      console.error(error)
      $q.notify({
        type: 'negative',
        message: 'Failed to send message. Check EmailJS template or credentials.',
      })
    })
}

const benefits = [
  {
    icon: 'collections_bookmark',
    title: 'Deck Management',
    desc: 'Easily organize all your decks in one place.',
  },
  {
    icon: 'inventory',
    title: 'Collection Tracking',
    desc: 'Keep track of all cards you own across sets.',
  },
  {
    icon: 'public',
    title: 'Community Decks',
    desc: 'Discover trending decks and share your own builds.',
  },
]

const testimonials = [
  {
    quote: 'ScryForge helped me prep for tournaments faster than ever.',
    name: 'MTG Arena Grinder',
  },
  {
    quote: 'I finally have a clear view of my whole collection.',
    name: 'Commander Fanatic',
  },
  {
    quote: 'Simple, beautiful, and effective.',
    name: 'Modern Player',
  },
]

const faqs = [
  {
    q: 'Is ScryForge free?',
    a: 'Yes! You can build decks and track your collection completely free.',
  },
  {
    q: 'Can I use it on mobile?',
    a: 'Absolutely. ScryForge works seamlessly on phones and tablets.',
  },
  {
    q: 'Does it support Commander format?',
    a: 'Of course! We support all major MTG formats.',
  },
]

const problems = [
  {
    question: 'Do you lose track of your decklists?',
    answer: 'ScryForge saves and organizes every deck you build.',
  },
  {
    question: 'Want to find new card ideas?',
    answer: 'Browse public decks by format, theme, or popularity.',
  },
  {
    question: 'Need to know how many copies you own?',
    answer: 'Track quantities with our collection manager.',
  },
  {
    question: 'Hate exporting to Excel?',
    answer: 'No spreadsheets needed – everything is managed visually.',
  },
]
</script>

<style>
@import 'https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css';

.bg-dark {
  background: radial-gradient(circle at top center, #1e1e1e, #0a0a0a);
  color: #ffffff;
}

/* Hero */
.hero-img-wrapper {
  position: relative;
  border-radius: 25px;
  overflow: hidden;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.6);
  max-height: 450px;
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
  justify-content: center;
  padding-top: 0;
  padding-bottom: 0;
  align-items: center;
  text-align: center;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.5), transparent 70%);
}

.hero-title {
  font-size: 2rem;
  font-weight: 700;
}

.hero-subtitle {
  font-size: 1rem;
  opacity: 0.8;
}

/* Cards / Glass */
.q-card,
.testimonial-card {
  background: rgba(35, 35, 35, 0.85);
  border: 1px solid rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(12px);
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.4);
  transition: all 0.25s ease;
  border-radius: 16px;
}

.q-card:hover,
.testimonial-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 4px 20px rgba(0, 255, 255, 0.1);
}

.testimonial-card {
  min-height: 160px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
}

/* FAQ Arrow Fix + Animation */
.faq-item .q-expansion-item__toggle-icon {
  margin-left: auto !important;
  margin-right: 16px !important;
  color: #00e6e6;
  transition: transform 0.3s ease;
}

.faq-item .q-expansion-item__toggle-icon:hover {
  transform: scale(1.2) rotate(90deg);
}

.faq-item .q-expansion-item__container:hover {
  background-color: rgba(255, 255, 255, 0.05);
}

/* Inputs + Forms */
.q-input,
.q-textarea {
  border-radius: 10px;
  background-color: rgba(40, 40, 40, 0.9);
  backdrop-filter: blur(6px);
  transition: box-shadow 0.2s ease;
}

.q-input:hover,
.q-textarea:hover {
  box-shadow: 0 0 0 2px rgba(0, 255, 255, 0.3);
}

/* Buttons */
.q-btn {
  padding: 12px 28px;
  font-size: 14px;
  font-weight: 600;
  border-radius: 50px;
  transition: all 0.25s ease;
  box-shadow: 0 0 0 rgba(0, 255, 255, 0);
}

.q-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 0 8px rgba(0, 255, 255, 0.3);
}

/* White buttons with neon glow */
.q-btn.bg-white:hover {
  box-shadow: 0 0 12px rgba(255, 255, 255, 0.4);
}

.hero_btn {
  width: 160px;
}

/* Responsive button group */
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

  .q-btn {
    width: 100%;
  }

  .q-btn + .q-btn {
    margin-top: 8px;
  }
}
</style>
