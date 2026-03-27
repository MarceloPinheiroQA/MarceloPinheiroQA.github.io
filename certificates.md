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
    /* Impede que os clones do loop criem uma barra de rolagem horizontal */
    overflow: hidden; 
  }

  /* Estilização das setas (Brancas com fundo azul sutil) */
  .swiper-button-next, .swiper-button-prev {
    color: #ffffff !important;
    background: rgba(16, 197, 248, 0.2);
    width: 45px;
    height: 45px;
    border-radius: 50%;
    z-index: 100;
  }

  .swiper-button-next:after, .swiper-button-prev:after {
    font-size: 18px;
  }

  .swiper {
    width: 100%;
    padding-top: 30px !important;
    padding-bottom: 70px !important;
  }

  .swiper-slide {
    width: 320px; 
    /* Transição suave para escala e brilho */
    transition: all 0.7s cubic-bezier(0.4, 0, 0.2, 1) !important;
    filter: brightness(0.3);
    transform: scale(0.8);
    opacity: 0.6;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  /* O SEGREDO: O slide que estiver com a classe 'active' ganha destaque total */
  .swiper-slide-active {
    filter: brightness(1);
    transform: scale(1.1);
    opacity: 1;
    z-index: 10;
  }

  .swiper-slide img {
    width: 100%;
    border-radius: 8px;
    box-shadow: 0 15px 45px rgba(0,0,0,0.8);
    display: block;
  }

  /* Legenda Branca e Fina (Estilo Formulário) */
  #cert-caption {
    text-align: center;
    font-weight: 300; 
    font-size: 1.4rem;
    color: #ffffff !important;
    margin-top: 20px;
    min-height: 1.8em;
    transition: opacity 0.4s ease;
    font-family: inherit;
  }

  .swiper-pagination-bullet-active {
    background: #10c5f8 !important;
  }
</style>

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

<script>
  const caption = document.getElementById('cert-caption');

  const swiper = new Swiper(".myCircularSwiper", {
    // Trocamos o efeito para slide simples para permitir a centralização circular
    effect: "slide",
    grabCursor: true,
    centeredSlides: true, //