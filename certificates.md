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
  }

  /* Ajuste das setas para ficarem visíveis no seu fundo azul */
  .swiper-button-next, .swiper-button-prev {
    color: #ffffff !important;
    background: rgba(16, 197, 248, 0.2); /* Fundo azul clarinho transparente */
    width: 50px;
    height: 50px;
    border-radius: 50%;
    z-index: 100;
  }

  .swiper-button-next:after, .swiper-button-prev:after {
    font-size: 20px;
    font-weight: bold;
  }

  .swiper {
    width: 100%;
    padding-bottom: 60px !important;
  }

  .swiper-slide {
    width: 320px; 
    transition: all 0.6s ease-in-out;
    filter: brightness(0.4);
    transform: scale(0.9);
  }

  /* Destaque do certificado central */
  .swiper-slide-active {
    filter: brightness(1);
    transform: scale(1.1);
  }

  .swiper-slide img {
    width: 100%;
    border-radius: 8px;
    box-shadow: 0 15px 40px rgba(0,0,0,0.7);
    display: block;
  }

  /* Legenda no Azul do Site */
  #cert-caption {
    text-align: center;
    font-size: 1.6rem;
    font-weight: bold;
    color: #10c5f8; 
    margin-top: 30px;
    min-height: 1.8em;
    transition: opacity 0.3s ease;
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

    </div>

    <div class="swiper-button-next"></div>
    <div class="swiper-button-prev"></div>
    <div class="swiper-pagination"></div>
  </div>

  <div id="cert-caption">Loading...</div>
</div>

<script>
  // Inicialização forçada para funcionar com poucos slides
  const caption = document.getElementById('cert-caption');

  const swiper = new Swiper(".mySwiper", {
    effect: "coverflow",
    grabCursor: true,
    centeredSlides: true,
    slidesPerView: "auto",
    loop: true, 
    speed: 900, // Transição mais lenta
    autoplay: {
      delay: 5000, // 5 segundos
      disableOnInteraction: false, // Não para se você clicar
    },
    coverflowEffect: {
      rotate: 15,
      stretch: 0,
      depth: 100,
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
        // Pega o nome do primeiro slide
        const initialSlide = this.slides[this.activeIndex];
        caption.innerText = initialSlide.getAttribute('data-name');
      },
      slideChange: function () {
        // Atualiza conforme troca
        const activeSlide = this.slides[this.activeIndex];
        if (activeSlide) {
          const title = activeSlide.getAttribute('data-name');
          caption.style.opacity = 0;
          setTimeout(() => {
            caption.innerText = title;
            caption.style.opacity = 1;
          }, 200);
        }
      }
    }
  });
</script>