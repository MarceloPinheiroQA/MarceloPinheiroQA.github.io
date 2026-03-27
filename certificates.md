---
layout: page
title: Certificates
---

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>

<style>
  .cert-container {
    width: 100%;
    margin: 40px auto;
    position: relative;
    overflow: hidden;
  }

  /* Setas customizadas com o azul do seu site */
  .swiper-button-next, .swiper-button-prev {
    color: #ffffff !important;
    background: rgba(16, 197, 248, 0.3);
    width: 45px;
    height: 45px;
    border-radius: 50%;
    transition: 0.3s;
  }

  .swiper-button-next:hover, .swiper-button-prev:hover {
    background: rgba(16, 197, 248, 0.6);
  }

  .swiper-button-next:after, .swiper-button-prev:after {
    font-size: 18px;
    font-weight: bold;
  }

  .swiper {
    width: 100%;
    padding-top: 20px !important;
    padding-bottom: 60px !important;
  }

  .swiper-slide {
    width: 320px; 
    /* Transição suave de 0.8s com curva de aceleração elegante */
    transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1) !important;
    filter: brightness(0.3) grayscale(50%);
    transform: scale(0.85);
  }

  /* Destaque do certificado central */
  .swiper-slide-active {
    filter: brightness(1) grayscale(0);
    transform: scale(1.1);
    z-index: 10;
  }

  .swiper-slide img {
    width: 100%;
    border-radius: 8px;
    box-shadow: 0 20px 50px rgba(0,0,0,0.8);
    display: block;
  }

  /* Legenda Branca, Fina (300) e usando a fonte do tema */
  #cert-caption {
    text-align: center;
    font-weight: 300; 
    font-size: 1.4rem;
    color: #ffffff !important;
    margin-top: 40px;
    min-height: 1.8em;
    transition: opacity 0.4s ease;
    font-family: inherit;
    letter-spacing: 0.5px;
  }

  .swiper-pagination-bullet-active {
    background: #10c5f8 !important;
  }
</style>

<div class="cert-container">
  <div class="swiper mySwiper">
    <div class="swiper-wrapper">
      
      <div class="swiper-slide" data-name="Certified Tester Foundation Level (CTFL)">
        <img src="assets/certificados/ctfl.png" alt="CTFL">
      </div>

      <div class="swiper-slide" data-name="Certified Tester Foundation Level - Agile Tester (CTFL-AT)">
        <img src="assets/certificados/ctfl-at.jpg" alt="CTFL-AT">
      </div>

      <div class="swiper-slide" data-name="Cambridge FCE">
        <img src="assets/certificados/fce.jpg" alt="FCE">
      </div>

    </div>

    <div class="swiper-button-next"></div>
    <div class="swiper-button-prev"></div>
    <div class="swiper-pagination"></div>
  </div>

  <div id="cert-caption">Loading...</div>
</div>

<script>
  const caption = document.getElementById('cert-caption');

  const swiper = new Swiper(".mySwiper", {
    effect: "coverflow",
    grabCursor: true,
    centeredSlides: true,
    slidesPerView: "auto",
    loop: true,
    loopedSlides: 3, // Importante para 3 slides não bugarem no loop
    speed: 1000, // Movimento bem suave (1 segundo)
    autoplay: {
      delay: 5000,
      disableOnInteraction: false,
    },
    coverflowEffect: {
      rotate: 0, // Removi a rotação para os slides não "entortarem" ao fundo
      stretch: 50, // Espaçamento entre certificados lateralmente
      depth: 150, // Profundidade 3D
      modifier: 1,
      slideShadows: false,
    },
    navigation: {
      nextEl: ".swiper-button-next",
      prevEl: ".swiper-button-prev",
    },
    pagination: {
      el: ".swiper-pagination",
      clickable: true,
    },
    on: {
      init: function () {
        // Correção para pegar o nome no loop infinito
        const activeSlide = this.slides[this.activeIndex];
        caption.innerText = activeSlide.getAttribute('data-name');
      },
      slideChange: function () {
        const activeSlide = this.slides[this.activeIndex];
        if (activeSlide) {
          const title = activeSlide.getAttribute('data-name');
          caption.style.opacity = 0;
          setTimeout(() => {
            caption.innerText = title;
            caption.style.opacity = 1;
          }, 300);
        }
      }
    }
  });
</script>