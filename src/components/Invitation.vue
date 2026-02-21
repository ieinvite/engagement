<template>
  <div class="container">
    <div class="hero">
      <video autoplay class="bg-video" loop muted playsinline>
        <source src="/video/background.mp4" type="video/mp4" />
      </video>

      <div class="hero-content">
        <h1 class="names">
          <div class="name-line">
            <span
              v-for="(letter, index) in 'Irem'.split('')"
              :key="'i' + index"
              :style="{ animationDelay: index * 0.15 + 's' }"
              class="letter"
            >
              {{ letter }}
            </span>
          </div>

          <div class="name-line and-line">
            <span class="letter" style="animation-delay: 0.6s">&</span>
          </div>

          <div class="name-line">
            <span
              v-for="(letter, index) in 'Enes'.split('')"
              :key="'e' + index"
              :style="{ animationDelay: index * 0.15 + 0.8 + 's' }"
              class="letter"
            >
              {{ letter }}
            </span>
          </div>
        </h1>

        <Divider align="center" class="fade-on-scroll" type="solid">
          <i class="pi pi-star-fill divider-icon" />
        </Divider>

        <p class="date-text fade-on-scroll">16 Mayıs 2026</p>
      </div>

      <div class="scroll-indicator">
        <div>Detaylar için lütfen kaydırın</div>
        <i class="pi pi-angle-down scroll-icon" />
      </div>
    </div>

    <div>
      <div class="invitation-card fade-on-scroll">
        <Card class="info-card">
          <template #title>
            <img class="doodle-top-center" src="/doodle/floral-thin-spirals.svg" />

            <p class="invitation-title">Nişanımıza Davetlisiniz</p>
          </template>

          <template #content>
            <div class="invitation-text fade-on-scroll">
              <p>
                Hayatlarımızı birleştirme yolunda attığımız bu özel adımda, mutluluğumuzu bizim için
                kıymetli olan aile büyüklerimiz ve dostlarımızla paylaşmanın heyecanını yaşıyoruz.
              </p>
              <p>Nişan törenimizde sizleri de aramızda görmekten onur ve mutluluk duyarız.</p>
            </div>

            <img class="doodle-bottom-center" src="/doodle/floral-thin-spirals-mirrored.svg" />
          </template>
        </Card>
      </div>

      <div class="countdown fade-on-scroll">
        <Card class="countdown-inner">
          <template #title>
            <p class="countdown-text">Nişan Tarihimize Kalan Süre</p>
          </template>

          <template #content>
            <div class="countdown-grid fade-on-scroll">
              <Card class="time-card">
                <template #content>
                  <div class="time-value">{{ days }}</div>
                  <div class="time-label">Gün</div>
                </template>
              </Card>

              <Card class="time-card fade-on-scroll">
                <template #content>
                  <div class="time-value">{{ hours }}</div>
                  <div class="time-label">Saat</div>
                </template>
              </Card>

              <Card class="time-card fade-on-scroll">
                <template #content>
                  <div class="time-value">{{ minutes }}</div>
                  <div class="time-label">Dakika</div>
                </template>
              </Card>

              <Card class="time-card fade-on-scroll">
                <template #content>
                  <div class="time-value">{{ seconds }}</div>
                  <div class="time-label">Saniye</div>
                </template>
              </Card>
            </div>
          </template>
        </Card>
      </div>

      <Card class="map-outer-card fade-on-scroll">
        <template #content>
          <img class="doodle-top-right" src="/doodle/floral-corner.svg" />

          <div class="map-inner-card fade-on-scroll">
            <Card class="map-content-card">
              <template #content>
                <h2 class="map-title">📍 Konum Bilgisi</h2>

                <p class="venue-name">Erdal İnönü Parkı Organizasyon Alanı</p>

                <p class="venue-address">
                  Lara park, Şirinyalı, Lara Cd. No:26, 07160 Muratpaşa/Antalya, Türkiye
                </p>

                <div class="map-container">
                  <iframe
                    :src="location"
                    class="map-frame"
                    height="300"
                    loading="lazy"
                    width="100%"
                  ></iframe>
                </div>

                <Button
                  class="map-button"
                  icon="pi pi-map"
                  label="    Google Maps'te Aç"
                  rounded
                  variant="outlined"
                  @click="openMaps"
                />
              </template>
            </Card>
          </div>

          <img class="doodle-bottom-left" src="/doodle/floral-corner-mirrored.svg" />
        </template>
      </Card>

      <Card class="faq-card fade-on-scroll">
        <template #title>
          <p class="faq-title">Önemli Bilgiler</p>
        </template>

        <template #content>
          <Accordion value="">
            <AccordionPanel value="0">
              <AccordionHeader>Header I</AccordionHeader>
              <AccordionContent>
                <p class="m-0">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
                  incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud
                  exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute
                  irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
                  pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui
                  officia deserunt mollit anim id est laborum.
                </p>
              </AccordionContent>
            </AccordionPanel>
            <AccordionPanel value="1">
              <AccordionHeader>Header II</AccordionHeader>
              <AccordionContent>
                <p class="m-0">
                  Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium
                  doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore
                  veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam
                  voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur
                  magni dolores eos qui ratione voluptatem sequi nesciunt. Consectetur, adipisci
                  velit, sed quia non numquam eius modi.
                </p>
              </AccordionContent>
            </AccordionPanel>
            <AccordionPanel value="2">
              <AccordionHeader>Header III</AccordionHeader>
              <AccordionContent>
                <p class="m-0">
                  At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis
                  praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias
                  excepturi sint occaecati cupiditate non provident, similique sunt in culpa qui
                  officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem
                  rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta nobis est
                  eligendi optio cumque nihil impedit quo minus.
                </p>
              </AccordionContent>
            </AccordionPanel>
          </Accordion>

          <img class="closing-doodle" src="/doodle/floral-spirals-symmetry.svg" />
        </template>
      </Card>
    </div>
  </div>
</template>

<script setup>
  import { onMounted, onUnmounted, ref } from 'vue'

  const location =
    'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3192.210437980804!2d30.72532957530592!3d36.86138146424924!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x14c39b00696c1a13%3A0x6d231fdb011b2132!2zRXJkYWwgxLBuw7Zuw7wgUGFya8SxIE9yZ2FuaXphc3lvbiBBbGFuxLE!5e0!3m2!1str!2sus!4v1771692598014!5m2!1str!2sus'

  const targetDate = new Date('2026-05-16T19:00:00')

  const days = ref(0)
  const hours = ref(0)
  const minutes = ref(0)
  const seconds = ref(0)

  let interval

  const updateCountdown = () => {
    const now = new Date()
    const diff = targetDate - now

    if (diff <= 0) return

    days.value = Math.floor(diff / (1000 * 60 * 60 * 24))
    hours.value = Math.floor((diff / (1000 * 60 * 60)) % 24)
    minutes.value = Math.floor((diff / (1000 * 60)) % 60)
    seconds.value = Math.floor((diff / 1000) % 60)
  }

  onMounted(() => {
    updateCountdown()
    interval = setInterval(updateCountdown, 1000)

    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible')
          }
        })
      },
      {
        threshold: 0.2,
      },
    )
    document.querySelectorAll('.fade-on-scroll').forEach((el) => {
      observer.observe(el)
    })
  })

  onUnmounted(() => {
    clearInterval(interval)
  })

  const openMaps = () => {
    window.open(location)
  }
</script>

<style scoped>
  .container {
    width: 100%;
    min-height: 100vh;
    background: lightgoldenrodyellow;
  }

  .hero {
    position: relative;
    height: 100vh;
    width: 100%;
    overflow: hidden;
  }

  .names {
    font-family: 'Monsieur La Doulaise', cursive;
    color: white;
    text-align: center;
    letter-spacing: 0.08em;
    text-shadow:
      0 0 10px rgba(255, 255, 255, 0.3),
      0 0 20px rgba(255, 255, 255, 0.2),
      0 0 40px rgba(255, 255, 255, 0.1);
  }

  .name-line {
    display: block;
    line-height: 1.2;
  }

  .and-line {
    font-size: 20px;
    font-weight: bold;
    margin: 10px 0;
    opacity: 0.9;
  }

  .letter {
    opacity: 0;
    display: inline-block;
    animation: letterFade 0.8s forwards;
  }

  @keyframes letterFade {
    from {
      opacity: 0;
      transform: translateY(40px);
      filter: blur(12px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
      filter: blur(0);
    }
  }

  .bg-video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 0;
  }

  .hero-content {
    position: relative;
    z-index: 1;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: white;
  }

  .divider-icon {
    color: floralwhite;
    margin-top: 3px;
  }

  .date-text {
    opacity: 0.8 !important;
  }

  .scroll-indicator {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    color: white;
    z-index: 2;
    text-align: center;
    font-size: 12px;
    animation: bounce 2s infinite;
    opacity: 0.9;
    letter-spacing: 1px;
    font-weight: 300;
  }

  @keyframes bounce {
    0%,
    100% {
      transform: translate(-50%, 0);
    }
    50% {
      transform: translate(-50%, 10px);
    }
  }

  .scroll-icon {
    color: white;
    opacity: 0.9;
  }

  :deep(.p-divider-content) {
    background: none !important;
  }

  :deep(.p-divider-horizontal) {
    width: 50% !important;
  }

  .invitation-card {
    padding: 60px 30px 60px;
    text-align: center;
    border-radius: 0;
    background: lightgoldenrodyellow;
  }

  .invitation-title {
    font-size: 36px;
    font-family: 'Imperial Script', cursive;
  }

  .invitation-text {
    font-size: 16px;
  }

  .info-card {
    position: relative;
    padding: 40px 0 80px;
  }

  .doodle-top-center {
    position: absolute;
    top: 10px;
    left: 50%;
    transform: translateX(-50%);
    width: 75px;
    opacity: 0.9;
    pointer-events: none;
  }

  .doodle-bottom-center {
    position: absolute;
    bottom: 10px;
    left: 50%;
    transform: translateX(-50%);
    width: 75px;
    opacity: 0.9;
    pointer-events: none;
  }

  .countdown {
    padding: 60px 30px 70px;
    text-align: center;
    border-radius: 0;
    background: #8bbf56;
  }

  .countdown-inner {
    background: #b4e087;
    position: relative;
    padding: 20px 0 60px;
  }

  .countdown-text {
    font-size: 22px;
    color: #2c4f09;
    text-shadow: #b4e087 1px 0 1px;
  }

  .countdown-grid {
    display: grid;
    grid-template-columns: repeat(2, 140px);
    gap: 10px;
    justify-content: center;
  }

  .time-card {
    text-align: center;
    border-radius: 16px;
    background: #4b8017;
  }

  .time-value {
    font-size: 36px;
    font-weight: bold;
    color: #d1f5ae;
    text-shadow: 1px 1px 3px #d2d2d2;
  }

  .time-label {
    font-size: 16px;
    margin-top: 5px;
    opacity: 0.7;
    color: #d1f5ae;
    text-shadow: 1px 1px 3px #d2d2d2;
  }

  .map-outer-card {
    text-align: center;
    border-radius: 0;
    background: #d4b4e8;
  }

  .map-inner-card {
    padding: 60px 20px;
    text-align: center;
  }

  .map-content-card {
    max-width: 500px;
    margin: 0 auto 30px auto;
    border-radius: 20px;
  }

  .map-title {
    font-size: 24px;
    margin-bottom: 10px;
    color: #946896 !important;
  }

  .venue-name {
    font-weight: 600;
    font-size: 18px;
    margin-bottom: 5px;
  }

  .venue-address {
    opacity: 0.8;
    margin-bottom: 15px;
  }

  .map-frame {
    border: 0;
    border-radius: 12px;
  }

  .map-button {
    display: inline-block;
    padding: 10px 20px;
    background: white;
    color: #946896;
    border-color: #946896 !important;
    border-radius: 30px;
    margin-top: 10px;
    text-decoration: none;
    transition: 0.3s;
  }

  .map-button:hover {
    opacity: 0.85;
  }

  .map-container iframe {
    border-radius: 20px;
  }

  .doodle-top-right,
  .doodle-bottom-left {
    position: absolute;
    width: 90px;
    opacity: 0.85;
    pointer-events: none;
  }

  .doodle-top-right {
    top: -15px;
    right: -15px;
  }

  .doodle-bottom-left {
    bottom: -15px;
    left: -15px;
  }

  :deep(.p-button-outlined:not(:disabled):hover) {
    background: rgba(212, 180, 232, 0.62);
    border-color: #946896;
    color: #946896;
  }

  .faq-card {
    text-align: center;
    border-radius: 0;
    background: #ffaec9;
  }

  .faq-title {
    color: #ba5170;
  }

  :deep(.p-accordionheader) {
    background-color: #ffd9e5;
  }

  :deep(.p-accordionpanel:not(.p-disabled).p-accordionpanel-active .p-accordionheader:hover) {
    background: #ffd9e5;
  }

  :deep(.p-accordionpanel:not(.p-accordionpanel-active):not(.p-disabled) .p-accordionheader:hover) {
    background: #ffd9e5;
  }

  :deep(.p-accordioncontent .p-accordioncontent-content .m-0) {
    margin-top: 0;
  }

  .fade-on-scroll {
    opacity: 0;
    transform: translateY(40px);
    filter: blur(10px);
    transition:
      opacity 1.2s ease,
      transform 1.2s ease,
      filter 1.2s ease;
  }

  .fade-on-scroll.visible {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }

  .closing-doodle {
    margin-top: 10px;
    width: 50px;
    opacity: 0;
    animation: closingFade 2s ease forwards;
    animation-delay: 0.5s;
  }

  @keyframes closingFade {
    from {
      opacity: 0;
      transform: translateY(30px);
      filter: blur(8px);
    }
    to {
      opacity: 0.9;
      transform: translateY(0);
      filter: blur(0);
    }
  }
</style>