<script setup lang="ts">
import { computed } from 'vue'
import { useLocaleStore } from '../stores/locale'
import { useScrollReveal } from '../composables/useScrollReveal'
import type { Lang } from '../data/translations'

useScrollReveal('.reveal')

const localeStore = useLocaleStore()
const locale = computed(() => localeStore.lang as Lang)

const langs = [
  { code: 'ca' as Lang, label: 'CA' },
  { code: 'es' as Lang, label: 'ES' },
  { code: 'en' as Lang, label: 'EN' },
]
function setLocale(code: Lang) { localeStore.setLang(code) }
function isActiveLang(code: Lang) { return locale.value === code }

const tx = computed(() => {
  const map: Record<Lang, Record<string, string>> = {
    es: {
      backGroup: '← Lumify Group',
      eyebrow: 'Lumify Logistics · Transporte & Montaje',
      heroTitle: 'Transporte profesional para tu empresa',
      heroDesc: 'Servicio de transporte de mercancías y montaje para empresas en Cataluña y la Península. Puntualidad, cuidado y compromiso en cada entrega.',
      ctaContact: 'Contactar ahora',
      servsLabel: 'Nuestros Servicios',
      servsTitle: 'Soluciones logísticas integrales',
      s1Title: 'Transporte de mercancías',
      s1Desc: 'Transporte seguro y puntual de mercancías para empresas. Rutas en Cataluña y por toda la Península Ibérica.',
      s2Title: 'Servicio de montaje',
      s2Desc: 'Montaje e instalación profesional de mobiliario, equipamiento e infraestructura para todo tipo de negocios.',
      s3Title: 'Cobertura amplia',
      s3Desc: 'Operamos en toda Cataluña y en la Península. Servicio adaptado a las necesidades de cada cliente.',
      contactLabel: 'Contacto',
      contactTitle: '¿Necesitas un presupuesto?',
      contactDesc: 'Ponte en contacto con nosotros. Te respondemos en menos de 24 horas laborables.',
      contactPhone: 'Teléfono',
      contactEmail: 'Email',
      footCopy: '© 2025 Lumify Group SL. Todos los derechos reservados.',
    },
    ca: {
      backGroup: '← Lumify Group',
      eyebrow: 'Lumify Logistics · Transport & Muntatge',
      heroTitle: 'Transport professional per a la teva empresa',
      heroDesc: 'Servei de transport de mercaderies i muntatge per a empreses a Catalunya i la Península. Puntualitat, cura i compromís en cada lliurament.',
      ctaContact: 'Contactar ara',
      servsLabel: 'Els nostres Serveis',
      servsTitle: 'Solucions logístiques integrals',
      s1Title: 'Transport de mercaderies',
      s1Desc: 'Transport segur i puntual de mercaderies per a empreses. Rutes a Catalunya i per tota la Península Ibèrica.',
      s2Title: 'Servei de muntatge',
      s2Desc: 'Muntatge i instal·lació professional de mobiliari, equipament i infraestructura per a tot tipus de negocis.',
      s3Title: 'Cobertura àmplia',
      s3Desc: 'Operem a tota Catalunya i a la Península. Servei adaptat a les necessitats de cada client.',
      contactLabel: 'Contacte',
      contactTitle: 'Necessites un pressupost?',
      contactDesc: 'Posa\'t en contacte amb nosaltres. Et responem en menys de 24 hores laborables.',
      contactPhone: 'Telèfon',
      contactEmail: 'Email',
      footCopy: '© 2025 Lumify Group SL. Tots els drets reservats.',
    },
    en: {
      backGroup: '← Lumify Group',
      eyebrow: 'Lumify Logistics · Transport & Assembly',
      heroTitle: 'Professional transport for your business',
      heroDesc: 'Freight transport and assembly services for businesses across Catalonia and the Iberian Peninsula. Punctuality, care and commitment in every delivery.',
      ctaContact: 'Contact us',
      servsLabel: 'Our Services',
      servsTitle: 'Comprehensive logistics solutions',
      s1Title: 'Freight transport',
      s1Desc: 'Safe and reliable freight transport for businesses. Routes across Catalonia and the whole Iberian Peninsula.',
      s2Title: 'Assembly service',
      s2Desc: 'Professional assembly and installation of furniture, equipment and infrastructure for all types of businesses.',
      s3Title: 'Wide coverage',
      s3Desc: 'We operate across Catalonia and the Peninsula. Service adapted to each client\'s needs.',
      contactLabel: 'Contact',
      contactTitle: 'Need a quote?',
      contactDesc: 'Get in touch with us. We respond within 24 business hours.',
      contactPhone: 'Phone',
      contactEmail: 'Email',
      footCopy: '© 2025 Lumify Group SL. All rights reserved.',
    },
  }
  return map[locale.value] ?? map.es
})
</script>

<template>
  <div class="min-h-screen bg-[#060E14] text-white font-sans overflow-x-hidden">

    <!-- ── NAV ──────────────────────────────────────────────── -->
    <nav class="fixed top-0 left-0 right-0 z-50 flex items-center justify-between px-[5%] py-[18px]
                bg-[#060E14]/95 backdrop-blur-md border-b border-white/8">
      <div class="flex items-center gap-6">
        <!-- Back to group -->
        <a href="/" class="text-white/50 text-sm font-medium no-underline transition-colors hover:text-white hidden sm:block">
          {{ tx.backGroup }}
        </a>
        <!-- Division name -->
        <span class="font-heading text-xl font-extrabold text-white tracking-[-0.3px]">
          Lumify<span class="text-amber-400"> Logistics</span>
        </span>
      </div>
      <!-- Language switcher -->
      <div class="flex gap-1 bg-white/10 rounded-full p-1">
        <button
          v-for="l in langs"
          :key="l.code"
          type="button"
          class="min-h-[36px] min-w-[36px] flex items-center justify-center border-none text-xs font-semibold py-1 px-2.5 rounded-full transition-all duration-200 font-sans uppercase tracking-wider cursor-pointer"
          :class="isActiveLang(l.code) ? 'bg-amber-400 text-[#060E14]' : 'bg-transparent text-white/60'"
          @click="setLocale(l.code)"
        >
          {{ l.label }}
        </button>
      </div>
    </nav>

    <!-- ── HERO ──────────────────────────────────────────────── -->
    <section class="min-h-screen bg-deep relative overflow-hidden flex flex-col justify-center items-center text-center px-[5%] pt-[120px] pb-20">
      <div class="absolute inset-0 z-0 bg-[radial-gradient(ellipse_80%_60%_at_50%_50%,rgba(245,158,11,0.12)_0%,transparent_65%)]" />
      <div class="absolute inset-0 z-0 opacity-[0.06] bg-size-[60px_60px] bg-[linear-gradient(rgba(245,158,11,0.4)_1px,transparent_1px),linear-gradient(90deg,rgba(245,158,11,0.4)_1px,transparent_1px)]" />
      <div class="relative z-10 max-w-[720px] mx-auto">
        <div class="inline-flex items-center gap-2 bg-amber-400/15 border border-amber-400/35 text-amber-400 py-1.5 px-4 rounded-full text-xs font-semibold tracking-widest uppercase mb-7 animate-[fadeUp_0.8s_ease_both]">
          <span class="w-1.5 h-1.5 bg-amber-400 rounded-full animate-[pulse_2s_infinite]" />
          {{ tx.eyebrow }}
        </div>
        <h1 class="font-heading text-[clamp(2.2rem,5.5vw,3.8rem)] font-extrabold text-white leading-[1.1] tracking-[-1.2px] mb-6 animate-[fadeUp_0.8s_0.1s_ease_both]">
          {{ tx.heroTitle }}
        </h1>
        <p class="text-lg text-white/65 leading-[1.75] max-w-[560px] mx-auto mb-10 font-light animate-[fadeUp_0.8s_0.2s_ease_both]">
          {{ tx.heroDesc }}
        </p>
        <a
          href="#contacto"
          class="inline-flex items-center gap-2 bg-amber-400 text-[#060E14] py-4 px-8 rounded-full font-semibold text-base no-underline transition-all duration-[0.25s] hover:bg-amber-300 hover:-translate-y-0.5 hover:shadow-[0_12px_40px_rgba(245,158,11,0.35)] animate-[fadeUp_0.8s_0.3s_ease_both]"
        >
          {{ tx.ctaContact }}
        </a>
      </div>
    </section>

    <!-- ── SERVICES ──────────────────────────────────────────── -->
    <section id="servicios" class="py-[100px] px-[5%] bg-[#060E14]">
      <div class="max-w-[1000px] mx-auto">
        <div class="text-center mb-14 reveal">
          <div class="text-xs font-bold tracking-[2px] uppercase text-amber-400 mb-3">{{ tx.servsLabel }}</div>
          <h2 class="font-heading text-[clamp(1.8rem,4vw,2.6rem)] font-extrabold text-white leading-[1.1] tracking-[-0.8px]">
            {{ tx.servsTitle }}
          </h2>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <!-- Service 1 -->
          <div class="bg-[#0C1420] border border-white/10 rounded-[18px] p-7 reveal">
            <div class="w-12 h-12 rounded-xl bg-amber-400/15 border border-amber-400/25 flex items-center justify-center mb-5">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" class="text-amber-400">
                <rect x="1" y="3" width="15" height="13"/><polygon points="16 8 20 8 23 11 23 16 16 16 16 8"/><circle cx="5.5" cy="18.5" r="2.5"/><circle cx="18.5" cy="18.5" r="2.5"/>
              </svg>
            </div>
            <h3 class="font-heading text-lg font-bold text-white mb-2">{{ tx.s1Title }}</h3>
            <p class="text-sm text-white/55 leading-relaxed">{{ tx.s1Desc }}</p>
          </div>
          <!-- Service 2 -->
          <div class="bg-[#0C1420] border border-white/10 rounded-[18px] p-7 reveal">
            <div class="w-12 h-12 rounded-xl bg-amber-400/15 border border-amber-400/25 flex items-center justify-center mb-5">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" class="text-amber-400">
                <path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"/>
              </svg>
            </div>
            <h3 class="font-heading text-lg font-bold text-white mb-2">{{ tx.s2Title }}</h3>
            <p class="text-sm text-white/55 leading-relaxed">{{ tx.s2Desc }}</p>
          </div>
          <!-- Service 3 -->
          <div class="bg-[#0C1420] border border-white/10 rounded-[18px] p-7 reveal">
            <div class="w-12 h-12 rounded-xl bg-amber-400/15 border border-amber-400/25 flex items-center justify-center mb-5">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" class="text-amber-400">
                <circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/>
              </svg>
            </div>
            <h3 class="font-heading text-lg font-bold text-white mb-2">{{ tx.s3Title }}</h3>
            <p class="text-sm text-white/55 leading-relaxed">{{ tx.s3Desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ── CONTACT ────────────────────────────────────────────── -->
    <section id="contacto" class="py-[100px] px-[5%] bg-[linear-gradient(135deg,#0a3d62_0%,#0d4f7e_60%,#0a3558_100%)] relative overflow-hidden">
      <div class="absolute inset-0 z-0 pointer-events-none bg-[radial-gradient(ellipse_70%_70%_at_80%_50%,rgba(245,158,11,0.12)_0%,transparent_70%)]" />
      <div class="relative z-10 max-w-[700px] mx-auto text-center">
        <div class="reveal">
          <div class="text-xs font-bold tracking-[2px] uppercase text-amber-400 mb-3">{{ tx.contactLabel }}</div>
          <h2 class="font-heading text-[clamp(1.8rem,4vw,2.6rem)] font-extrabold text-white leading-[1.1] tracking-[-0.8px] mb-4">
            {{ tx.contactTitle }}
          </h2>
          <p class="text-base text-white/70 leading-[1.75] mb-12">{{ tx.contactDesc }}</p>
        </div>
        <div class="flex flex-col sm:flex-row gap-5 justify-center reveal">
          <!-- Phone -->
          <a
            href="tel:679818935"
            class="flex items-center gap-3 bg-white/10 border border-white/20 rounded-2xl px-7 py-5 no-underline transition-all hover:bg-white/15 hover:border-amber-400/40"
          >
            <div class="w-10 h-10 rounded-xl bg-amber-400/20 flex items-center justify-center shrink-0">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-amber-400">
                <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 13 19.79 19.79 0 0 1 1.65 4.4 2 2 0 0 1 3.62 2h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 9.91a16 16 0 0 0 6.16 6.16l.91-.91a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/>
              </svg>
            </div>
            <div class="text-left">
              <div class="text-xs text-white/50 uppercase tracking-wider font-medium">{{ tx.contactPhone }}</div>
              <div class="text-white font-semibold text-lg">679 818 935</div>
            </div>
          </a>
          <!-- Email -->
          <a
            href="mailto:logistics@lumify.es"
            class="flex items-center gap-3 bg-white/10 border border-white/20 rounded-2xl px-7 py-5 no-underline transition-all hover:bg-white/15 hover:border-amber-400/40"
          >
            <div class="w-10 h-10 rounded-xl bg-amber-400/20 flex items-center justify-center shrink-0">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-amber-400">
                <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/>
              </svg>
            </div>
            <div class="text-left">
              <div class="text-xs text-white/50 uppercase tracking-wider font-medium">{{ tx.contactEmail }}</div>
              <div class="text-white font-semibold text-base">logistics@lumify.es</div>
            </div>
          </a>
        </div>
      </div>
    </section>

    <!-- ── FOOTER ────────────────────────────────────────────── -->
    <footer class="bg-[#040A10] text-white/45 py-10 px-[5%] flex flex-col gap-3 items-center text-center border-t border-white/8">
      <div class="flex items-center gap-4">
        <a href="/" class="text-white/40 text-sm no-underline hover:text-white/70 transition-colors">← Lumify Group</a>
        <span class="text-white/20">|</span>
        <span class="font-heading text-base font-bold text-white">Lumify<span class="text-amber-400"> Logistics</span></span>
      </div>
      <p class="text-xs text-white/25">{{ tx.footCopy }}</p>
    </footer>

  </div>
</template>
