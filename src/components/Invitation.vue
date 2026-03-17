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

        <p class="date-text fade-on-scroll">27 Haziran 2026</p>
        <p class="date-text fade-on-scroll ">19:00</p>
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
                Hayatlarımızı birleştirme yolunda attığımız bu ilk adımda, mutluluğumuzu bizim için
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

                <p class="venue-name">Bereket Evi Organizasyon ve Etkinlik Salonları</p>

                <p class="venue-address">
                  Macun, Fabrika Sokak, No: 35, Aksu/Antalya
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
          <Accordion :multiple="true">
            <AccordionPanel value="0">
              <AccordionHeader>Organizasyon</AccordionHeader>
              <AccordionContent>
                <p class="m-0 padding-medium">
                  Nişan organizasyonumuz, siz değerli misafirlerimiz için hazırlanan özel bir akşam yemeği programı eşliğinde gerçekleşecektir.
                </p>

                <img class="food-doodle" src="/doodle/food-dish.svg" />
              </AccordionContent>
            </AccordionPanel>
            <AccordionPanel value="1">
              <AccordionHeader>Anılarınızı Bizimle Paylaşın</AccordionHeader>
              <AccordionContent>
                <div class="upload-section">
                  <p class="m-0">
                    Bu özel günde çektiğiniz fotoğrafları bizimle paylaşmak isterseniz aşağıdaki bağlantıyı kullanabilirsiniz.
                  </p>
                  <p class="m-0">
                    Sizin gözünüzden anılarımızı görmek bizi çok mutlu eder ✨
                  </p>

                  <div class="buttons">
                    <Button
                        label="    Fotoğraf Yükle"
                        icon="pi pi-upload"
                        class="upload-btn"
                        @click="openDrive"
                        rounded
                        variant="outlined"
                    />
                  </div>
                </div>
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
    'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3188.214344066977!2d30.837471675310397!3d36.95693735884953!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x14c3810f4b8bd8ed%3A0x4a4234bff5c0db93!2sBereket%20Evi%20Organizasyon%20ve%20Etkinlik%20Salonlar%C4%B1!5e0!3m2!1str!2sus!4v1773593325890!5m2!1str!2sus'

  const driveLink = 'https://forms.gle/g7j9SSCzoes4c5VVA'

  const targetDate = new Date('2026-06-27T19:00:00')

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

  const openDrive = () => {
    window.open(driveLink, '_blank')
  }

  const openMaps = () => {
    window.open(location)
  }
</script>

<style scoped>
  .container {
    width: 100%;
    min-height: 100vh;
    background: #261c0c;
  }

  .hero {
    position: relative;
    height: 100vh;
    width: 100%;
    overflow: hidden;
  }

  .names {
    font-family: 'Monsieur La Doulaise', cursive;
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
    color: #261c0c;
  }

  .divider-icon {
    color: #261c0c;
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
    color: #261c0c;
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
    color: #261c0c;
    opacity: 0.9;
  }

  :deep(.p-divider-content) {
    background: none !important;
  }

  :deep(.p-divider:before) {
    border-top: 1px solid #261c0c;
  }

  :deep(.p-divider-horizontal) {
    width: 50% !important;
  }

  .invitation-card {
    padding: 60px 30px 60px;
    text-align: center;
    border-radius: 0;
  }

  .invitation-title {
    font-size: 36px;
    font-family: 'Imperial Script', cursive;
    color: #261c0c;
  }

  .invitation-text {
    font-size: 16px;
    color: #261c0c;
  }

  .info-card {
    position: relative;
    padding: 40px 0 80px;
    background-color: #e7dccf;
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
    background: #c2ab90;
  }

  .countdown-inner {
    background: #e7dccf;
    position: relative;
    padding: 20px 0 60px;
  }

  .countdown-text {
    font-size: 22px;
    color: #261c0c;
    text-shadow: #dccdb9 1px 0 1px;
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
    background: #dccdb9;
  }

  .time-value {
    font-size: 36px;
    font-weight: bold;
    color: #261c0c;
    text-shadow: 1px 1px 3px #c2ab90;
  }

  .time-label {
    font-size: 16px;
    margin-top: 5px;
    opacity: 0.7;
    color: #261c0c;
    text-shadow: 1px 1px 3px #c2ab90;
  }

  .map-outer-card {
    text-align: center;
    border-radius: 0;
    background: #261c0c;
  }

  .map-inner-card {
    padding: 60px 20px;
    text-align: center;
  }

  .map-content-card {
    max-width: 500px;
    margin: 0 auto 30px auto;
    border-radius: 20px;
    background-color: #e7dccf;
  }

  .map-title {
    font-size: 24px;
    margin-bottom: 10px;
    color: #261c0c !important;
  }

  .venue-name {
    font-weight: 600;
    font-size: 18px;
    margin-bottom: 5px;
    color: #261c0c !important;
  }

  .venue-address {
    opacity: 0.8;
    margin-bottom: 15px;
    color: #261c0c !important;
  }

  .map-frame {
    border: 0;
    border-radius: 12px;
  }

  .map-button {
    display: inline-block;
    padding: 10px 20px;
    background: #e7dccf;
    color: #261c0c;
    border-color: #261c0c !important;
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
    background: rgba(194, 171, 144, 0.48);
    border-color: #261c0c;
    color: #261c0c;
  }

  .faq-card {
    text-align: center;
    border-radius: 0;
    background: #c2ab90;
  }

  .faq-title {
    color: #261c0c;
  }

  :deep(.p-accordionheader) {
    background-color: #e7dccf;
    color: #261c0c;
  }

  :deep(.p-accordionpanel:not(.p-disabled).p-accordionpanel-active .p-accordionheader:hover) {
    background: #e7dccf;
    color: #261c0c;
  }

  :deep(.p-accordionpanel:not(.p-accordionpanel-active):not(.p-disabled) .p-accordionheader:hover) {
    background: #e7dccf;
    color: #261c0c;
  }

  :deep(.p-accordionpanel:not(.p-disabled).p-accordionpanel-active > .p-accordionheader) {
    background: #e7dccf;
    color: #261c0c;
  }

  :deep(.p-accordioncontent .p-accordioncontent-content .m-0) {
    margin-top: 0;
    color: #261c0c;
  }

  :deep(.p-accordioncontent-content) {
    background: #eeeae5;
  }

  :deep(.p-accordionpanel:not(.p-disabled).p-accordionpanel-active > .p-accordionheader:hover .p-accordionheader-toggle-icon) {
    color: #261c0c;
  }
  :deep(.p-accordionpanel:not(.p-disabled).p-accordionpanel-active > .p-accordionheader:hover) {
    color: #261c0c;
  }

  :deep(.p-accordionheader-toggle-icon) {
    color: #261c0c;
  }

  .padding-medium {
    padding-top: 18px !important;
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

  .food-doodle {
    margin-top: 10px;
    width: 50px;
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

  .upload-section {
    text-align: center;
    padding: 10px 0;
  }

  .buttons {
    display: flex;
    justify-content: center;
    gap: 12px;
    margin-top: 15px;
    flex-wrap: wrap;
  }

  .upload-btn {
    display: inline-block;
    padding: 10px 20px;
    background: #e7dccf;
    color: #261c0c;
    border-color: #261c0c !important;
    border-radius: 30px;
    margin-top: 10px;
    text-decoration: none;
    transition: 0.3s;
  }

  .upload-btn:hover {
    transform: translateY(-2px) scale(1.05);
  }
</style>