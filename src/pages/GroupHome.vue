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

// ── Inline translations ──────────────────────────────────────────
const tx = computed(() => {
  const map: Record<Lang, Record<string, string>> = {
    es: {
      eyebrow: 'Lumify Group SL · Empresa Familiar',
      heroTitle: 'Soluciones para particulares y empresas',
      heroDesc:
        'Somos una empresa familiar con varias líneas de negocio especializadas. Te acompañamos desde la tecnología hasta la logística, pasando por el diseño técnico y la gestoría.',
      divisionsLabel: 'Nuestras Divisiones',
      divisionsTitle: 'Un grupo, múltiples soluciones',
      divisionsDesc:
        'Cada división está especializada en su área y orientada a dar un servicio de proximidad, tanto para particulares como para empresas.',
      techTag: 'Activo',
      techName: 'Lumify Tech',
      techSubtitle: 'Tecnología para empresas',
      techDesc:
        'Servicios tecnológicos dirigidos a startups, autónomos y PYMEs. PIM, ecommerce, gobierno de datos y syndication omnicanal.',
      techCta: 'Explorar →',
      logTag: 'Activo',
      logName: 'Lumify Logistics',
      logSubtitle: 'Transporte y montaje',
      logDesc:
        'Transporte de mercancías y servicio de montaje profesional para empresas en Cataluña y la Península.',
      logCta: 'Más información →',
      studioTag: 'Próximamente',
      studioName: 'Lumify Studio',
      studioSubtitle: 'Desarrollo técnico y gráfico',
      studioDesc:
        'Proyectos arquitectónicos: planos en 2D y 3D, renders y visualizaciones técnicas de alta calidad.',
      studioNote: 'En desarrollo',
      advisorsTag: 'Próximamente',
      advisorsName: 'Lumify Legal',
      advisorsSubtitle: 'Gestoría y derecho mercantil',
      advisorsDesc:
        'Servicios de gestoría para autónomos y empresas, junto con asesoramiento en derecho mercantil.',
      advisorsNote: 'En desarrollo',
      footDesc: 'Empresa familiar con múltiples líneas de negocio.',
      footCopy: '© 2025 Lumify Group SL. Todos los derechos reservados.',
    },
    ca: {
      eyebrow: 'Lumify Group SL · Empresa Familiar',
      heroTitle: 'Solucions per a particulars i empreses',
      heroDesc:
        'Som una empresa familiar amb diverses línies de negoci especialitzades. T\'acompanyem des de la tecnologia fins a la logística, passant pel disseny tècnic i la gestoria.',
      divisionsLabel: 'Les nostres Divisions',
      divisionsTitle: 'Un grup, múltiples solucions',
      divisionsDesc:
        'Cada divisió és especialitzada en la seva àrea i orientada a donar un servei de proximitat, tant per a particulars com per a empreses.',
      techTag: 'Actiu',
      techName: 'Lumify Tech',
      techSubtitle: 'Tecnologia per a empreses',
      techDesc:
        'Serveis tecnològics per a startups, autònoms i PIMEs. PIM, ecommerce, govern de dades i syndication omnicanal.',
      techCta: 'Explorar →',
      logTag: 'Actiu',
      logName: 'Lumify Logistics',
      logSubtitle: 'Transport i muntatge',
      logDesc:
        'Transport de mercaderies i servei de muntatge professional per a empreses a Catalunya i la Península.',
      logCta: 'Més informació →',
      studioTag: 'Pròximament',
      studioName: 'Lumify Studio',
      studioSubtitle: 'Desenvolupament tècnic i gràfic',
      studioDesc:
        'Projectes arquitectònics: plans en 2D i 3D, renders i visualitzacions tècniques d\'alta qualitat.',
      studioNote: 'En desenvolupament',
      advisorsTag: 'Pròximament',
      advisorsName: 'Lumify Legal',
      advisorsSubtitle: 'Gestoria i dret mercantil',
      advisorsDesc:
        'Serveis de gestoria per a autònoms i empreses, juntament amb assessorament en dret mercantil.',
      advisorsNote: 'En desenvolupament',
      footDesc: 'Empresa familiar amb múltiples línies de negoci.',
      footCopy: '© 2025 Lumify Group SL. Tots els drets reservats.',
    },
    en: {
      eyebrow: 'Lumify Group SL · Family Business',
      heroTitle: 'Solutions for individuals and businesses',
      heroDesc:
        'We are a family business with several specialised business lines. We support you from technology to logistics, including technical design and advisory services.',
      divisionsLabel: 'Our Divisions',
      divisionsTitle: 'One group, multiple solutions',
      divisionsDesc:
        'Each division is specialised in its field and focused on providing a local, personal service to both individuals and businesses.',
      techTag: 'Active',
      techName: 'Lumify Tech',
      techSubtitle: 'Technology for businesses',
      techDesc:
        'Technology services for startups, freelancers and SMEs. PIM, ecommerce, data governance and omnichannel syndication.',
      techCta: 'Explore →',
      logTag: 'Active',
      logName: 'Lumify Logistics',
      logSubtitle: 'Transport & assembly',
      logDesc:
        'Freight transport and professional assembly services for companies across Catalonia and the Iberian Peninsula.',
      logCta: 'Learn more →',
      studioTag: 'Coming soon',
      studioName: 'Lumify Studio',
      studioSubtitle: 'Technical & graphic design',
      studioDesc:
        'Architectural projects: 2D and 3D drawings, renders and high-quality technical visualisations.',
      studioNote: 'In development',
      advisorsTag: 'Coming soon',
      advisorsName: 'Lumify Legal',
      advisorsSubtitle: 'Advisory & business law',
      advisorsDesc:
        'Accounting and administration services for freelancers and companies, plus commercial and business law advisory.',
      advisorsNote: 'In development',
      footDesc: 'Family business with multiple business lines.',
      footCopy: '© 2025 Lumify Group SL. All rights reserved.',
    },
  }
  return map[locale.value] ?? map.es
})

</script>

<template>
  <div class="min-h-screen bg-[#060E14] text-white font-sans overflow-x-hidden">

    <!-- ── NAV GROUP ─────────────────────────────────────────── -->
    <nav class="fixed top-0 left-0 right-0 z-50 flex items-center justify-between px-[5%] py-[18px]
                bg-[#060E14]/95 backdrop-blur-md border-b border-white/8">
      <!-- Logo -->
      <a href="/" class="flex items-center gap-2 no-underline">
        <span class="font-heading text-xl font-extrabold text-white tracking-[-0.3px]">
          Lumify<span class="text-blue"> Group</span>
        </span>
      </a>

      <!-- Language switcher -->
      <div class="flex gap-1 bg-white/10 rounded-full p-1">
        <button
          v-for="l in langs"
          :key="l.code"
          type="button"
          class="min-h-[36px] min-w-[36px] flex items-center justify-center border-none text-xs font-semibold py-1 px-2.5 rounded-full transition-all duration-200 font-sans uppercase tracking-wider cursor-pointer"
          :class="isActiveLang(l.code) ? 'bg-blue text-white' : 'bg-transparent text-white/60'"
          @click="setLocale(l.code)"
        >
          {{ l.label }}
        </button>
      </div>
    </nav>

    <!-- ── HERO ──────────────────────────────────────────────── -->
    <section class="min-h-screen bg-deep relative overflow-hidden flex flex-col justify-center items-center text-center px-[5%] pt-[120px] pb-20">
      <!-- Radial gradient -->
      <div class="absolute inset-0 z-0 bg-[radial-gradient(ellipse_80%_60%_at_50%_50%,rgba(60,157,255,0.14)_0%,transparent_65%)]" />
      <!-- Grid -->
      <div class="absolute inset-0 z-0 opacity-[0.06] bg-size-[60px_60px] bg-[linear-gradient(rgba(60,157,255,0.5)_1px,transparent_1px),linear-gradient(90deg,rgba(60,157,255,0.5)_1px,transparent_1px)]" />

      <div class="relative z-10 max-w-[760px] mx-auto">
        <!-- Eyebrow -->
        <div class="inline-flex items-center gap-2 bg-blue/15 border border-blue/35 text-blue py-1.5 px-4 rounded-full text-xs font-semibold tracking-widest uppercase mb-7 animate-[fadeUp_0.8s_ease_both]">
          <span class="w-1.5 h-1.5 bg-blue rounded-full animate-[pulse_2s_infinite]" />
          {{ tx.eyebrow }}
        </div>

        <!-- Heading -->
        <h1 class="font-heading text-[clamp(2.4rem,6vw,4rem)] font-extrabold text-white leading-[1.08] tracking-[-1.5px] mb-6 animate-[fadeUp_0.8s_0.1s_ease_both]">
          {{ tx.heroTitle }}
        </h1>

        <!-- Description -->
        <p class="text-lg text-white/65 leading-[1.75] max-w-[600px] mx-auto mb-10 font-light animate-[fadeUp_0.8s_0.2s_ease_both]">
          {{ tx.heroDesc }}
        </p>

        <!-- CTA -->
        <a
          href="#divisiones"
          class="inline-flex items-center gap-2 bg-blue text-white py-4 px-8 rounded-full font-semibold text-base no-underline transition-all duration-[0.25s] hover:bg-[#5aaeff] hover:-translate-y-0.5 hover:shadow-[0_12px_40px_rgba(60,157,255,0.4)] animate-[fadeUp_0.8s_0.3s_ease_both]"
        >
          {{ tx.divisionsLabel }} ↓
        </a>
      </div>
    </section>

    <!-- ── DIVISIONS ─────────────────────────────────────────── -->
    <section id="divisiones" class="py-[100px] px-[5%] bg-[#060E14]">
      <div class="max-w-[1100px] mx-auto">

        <!-- Section header -->
        <div class="text-center mb-16 reveal">
          <div class="text-xs font-bold tracking-[2px] uppercase text-blue mb-3">{{ tx.divisionsLabel }}</div>
          <h2 class="font-heading text-[clamp(1.9rem,4vw,2.8rem)] font-extrabold text-white leading-[1.1] tracking-[-0.8px] mb-4">
            {{ tx.divisionsTitle }}
          </h2>
          <p class="text-base text-white/55 max-w-[560px] mx-auto leading-relaxed">
            {{ tx.divisionsDesc }}
          </p>
        </div>

        <!-- Cards grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">

          <!-- ── LUMIFY TECH ── -->
          <a
            href="/tech"
            class="group block no-underline bg-[#0C1420] border border-white/10 rounded-[20px] p-8 transition-all duration-300 hover:border-blue/50 hover:-translate-y-1 hover:shadow-[0_20px_50px_rgba(60,157,255,0.12)] reveal"
          >
            <!-- Icon -->
            <div class="w-14 h-14 rounded-2xl bg-blue/15 border border-blue/25 flex items-center justify-center mb-6 transition-colors group-hover:bg-blue/25">
              <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" class="text-blue">
                <polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/>
              </svg>
            </div>
            <!-- Badge -->
            <div class="inline-flex items-center gap-1.5 bg-emerald-500/15 border border-emerald-500/30 text-emerald-400 py-1 px-3 rounded-full text-[11px] font-bold uppercase tracking-widest mb-4">
              <span class="w-1.5 h-1.5 bg-emerald-400 rounded-full animate-[pulse_2s_infinite]" />
              {{ tx.techTag }}
            </div>
            <h3 class="font-heading text-2xl font-bold text-white mb-1">{{ tx.techName }}</h3>
            <p class="text-sm text-blue font-medium mb-3">{{ tx.techSubtitle }}</p>
            <p class="text-sm text-white/55 leading-relaxed mb-6">{{ tx.techDesc }}</p>
            <span class="text-sm font-semibold text-blue group-hover:text-[#5aaeff] transition-colors">
              {{ tx.techCta }}
            </span>
          </a>

          <!-- ── LUMIFY LOGISTICS ── -->
          <a
            href="/logistics"
            class="group block no-underline bg-[#0C1420] border border-white/10 rounded-[20px] p-8 transition-all duration-300 hover:border-amber-400/50 hover:-translate-y-1 hover:shadow-[0_20px_50px_rgba(245,158,11,0.10)] reveal"
          >
            <!-- Icon -->
            <div class="w-14 h-14 rounded-2xl bg-amber-400/15 border border-amber-400/25 flex items-center justify-center mb-6 transition-colors group-hover:bg-amber-400/25">
              <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" class="text-amber-400">
                <rect x="1" y="3" width="15" height="13"/><polygon points="16 8 20 8 23 11 23 16 16 16 16 8"/><circle cx="5.5" cy="18.5" r="2.5"/><circle cx="18.5" cy="18.5" r="2.5"/>
              </svg>
            </div>
            <!-- Badge -->
            <div class="inline-flex items-center gap-1.5 bg-emerald-500/15 border border-emerald-500/30 text-emerald-400 py-1 px-3 rounded-full text-[11px] font-bold uppercase tracking-widest mb-4">
              <span class="w-1.5 h-1.5 bg-emerald-400 rounded-full animate-[pulse_2s_infinite]" />
              {{ tx.logTag }}
            </div>
            <h3 class="font-heading text-2xl font-bold text-white mb-1">{{ tx.logName }}</h3>
            <p class="text-sm text-amber-400 font-medium mb-3">{{ tx.logSubtitle }}</p>
            <p class="text-sm text-white/55 leading-relaxed mb-6">{{ tx.logDesc }}</p>
            <span class="text-sm font-semibold text-amber-400 group-hover:text-amber-300 transition-colors">
              {{ tx.logCta }}
            </span>
          </a>

          <!-- ── LUMIFY STUDIO (próximamente) ── -->
          <div class="bg-[#0C1420]/60 border border-white/6 rounded-[20px] p-8 opacity-70 reveal">
            <!-- Icon -->
            <div class="w-14 h-14 rounded-2xl bg-violet-400/10 border border-violet-400/20 flex items-center justify-center mb-6">
              <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" class="text-violet-400/70">
                <line x1="18" y1="20" x2="8" y2="10"/><line x1="5" y1="3" x2="19" y2="3"/><line x1="6" y1="9" x2="3" y2="6"/><line x1="13" y1="6" x2="3" y2="16"/><path d="m5 19 7-7"/>
              </svg>
            </div>
            <!-- Badge -->
            <div class="inline-flex items-center gap-1.5 bg-white/8 border border-white/15 text-white/40 py-1 px-3 rounded-full text-[11px] font-bold uppercase tracking-widest mb-4">
              {{ tx.studioTag }}
            </div>
            <h3 class="font-heading text-2xl font-bold text-white/60 mb-1">{{ tx.studioName }}</h3>
            <p class="text-sm text-violet-400/60 font-medium mb-3">{{ tx.studioSubtitle }}</p>
            <p class="text-sm text-white/35 leading-relaxed mb-6">{{ tx.studioDesc }}</p>
            <span class="text-sm font-medium text-white/30">{{ tx.studioNote }}</span>
          </div>

          <!-- ── LUMIFY ADVISORS (próximamente) ── -->
          <div class="bg-[#0C1420]/60 border border-white/6 rounded-[20px] p-8 opacity-70 reveal">
            <!-- Icon -->
            <div class="w-14 h-14 rounded-2xl bg-teal-400/10 border border-teal-400/20 flex items-center justify-center mb-6">
              <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" class="text-teal-400/70">
                <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/>
              </svg>
            </div>
            <!-- Badge -->
            <div class="inline-flex items-center gap-1.5 bg-white/8 border border-white/15 text-white/40 py-1 px-3 rounded-full text-[11px] font-bold uppercase tracking-widest mb-4">
              {{ tx.advisorsTag }}
            </div>
            <h3 class="font-heading text-2xl font-bold text-white/60 mb-1">{{ tx.advisorsName }}</h3>
            <p class="text-sm text-teal-400/60 font-medium mb-3">{{ tx.advisorsSubtitle }}</p>
            <p class="text-sm text-white/35 leading-relaxed mb-6">{{ tx.advisorsDesc }}</p>
            <span class="text-sm font-medium text-white/30">{{ tx.advisorsNote }}</span>
          </div>

        </div>
      </div>
    </section>

    <!-- ── FOOTER ────────────────────────────────────────────── -->
    <footer class="bg-[#040A10] text-white/45 py-10 px-[5%] flex flex-col gap-4 items-center text-center border-t border-white/8">
      <span class="font-heading text-lg font-extrabold text-white">
        Lumify<span class="text-blue"> Group</span>
      </span>
      <p class="text-sm max-w-[300px] leading-relaxed">{{ tx.footDesc }}</p>
      <p class="text-xs text-white/30">{{ tx.footCopy }}</p>
    </footer>

  </div>
</template>
