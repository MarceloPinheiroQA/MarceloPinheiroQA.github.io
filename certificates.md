---
layout: page
title: Certificates
description: 'A collection of my professional certification.'
show_tile: false
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

  .swiper-button-next, .swiper-button-prev {
    color: #ffffff !important;
    background: rgba(16, 197, 248, 0.2);
    width: 45px;
    height: 45px;
    border-radius: 50%;
    z-index: 100;
  }

  .swiper {
    width: 100%;
    padding-top: 30px !important;
    padding-bottom: 70px !important;
  }

  .swiper-slide {
    width: 320px;
    filter: brightness(0.35);
    transform: scale(0.8);
    opacity: 0.45;
    will-change: transform, opacity, filter;
    transition:
      transform 0.45s cubic-bezier(0.4, 0, 0.2, 1),
      filter 0.45s cubic-bezier(0.4, 0, 0.2, 1),
      opacity 0.45s cubic-bezier(0.4, 0, 0.2, 1) !important;
  }

  .swiper-slide img {
    width: 100%;
    border-radius: 8px;
    box-shadow: 0 15px 45px rgba(0,0,0,0.8);
  }

  #cert-caption {
    text-align: center;
    font-weight: 300; 
    font-size: 1.4rem;
    color: #ffffff !important;
    margin-top: 20px;
    min-height: 1.8em;
    transition: opacity 0.4s ease;
  }

  .swiper-pagination-bullet-active {
    background: #10c5f8 !important;
  }

  .myCircularSwiper .swiper-wrapper {
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1) !important;
  }
</style>

<!-- Main -->
<div id="main" class="alt">
  <section id="one">
    <div class="inner">
      <header class="major">
        <h1>CERTIFICATES</h1>
      </header>

      <div class="cert-container">
        <div class="swiper myCircularSwiper">
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
    </div>
  </section>
</div>

<script>
  function updateText(swiperInstance) {
    const captionElement = document.getElementById('cert-caption');
    const activeSlide = swiperInstance.slides[swiperInstance.activeIndex];
    
    if (activeSlide && captionElement) {
      const title = activeSlide.getAttribute('data-name');
      captionElement.style.opacity = 0;
      setTimeout(() => {
        captionElement.innerText = title;
        captionElement.style.opacity = 1;
      }, 250);
    }
  }

  function updateSlideStates(swiperInstance) {
    swiperInstance.slides.forEach((slide) => {
      const progress = Math.max(Math.min(slide.progress, 2), -2);
      const absProgress = Math.abs(progress);

      const scale = 1.1 - Math.min(absProgress * 0.25, 0.4);
      const opacity = 1 - Math.min(absProgress * 0.5, 0.55);
      const brightness = 1 - Math.min(absProgress * 0.4, 0.65);

      slide.style.transform = `translate3d(0, 0, 0) scale(${scale})`;
      slide.style.opacity = opacity;
      slide.style.filter = `brightness(${brightness})`;
      slide.style.zIndex = String(100 - Math.round(absProgress * 10));
    });
  }

  const swiper = new Swiper(".myCircularSwiper", {
    effect: "slide",
    grabCursor: true,
    centeredSlides: true,
    slidesPerView: "auto",
    loop: true,
    loopAdditionalSlides: 3,
    watchSlidesProgress: true,
    speed: 950,
    autoplay: {
      delay: 7000,
      disableOnInteraction: false,
      pauseOnMouseEnter: true,
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
        this.updateSlidesProgress();
        updateSlideStates(this);
        updateText(this);
      },
      setTranslate: function () {
        updateSlideStates(this);
      },
      setTransition: function (speed) {
        this.slides.forEach((slide) => {
          slide.style.transitionDuration = `${speed}ms`;
        });
      },
      slideChangeTransitionEnd: function () {
        updateText(this);
      }
    }
  });
</script> 