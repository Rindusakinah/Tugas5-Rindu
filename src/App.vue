<template>
  <div>
    <header class="header">
      <div class="header-content">
        <h1>My Online Shop</h1>
      </div>
    </header>
    <div class="hero-section">
      <q-parallax :srcset="['/images/hero-bg.jpg']" />
      <div class="hero-text">
        <h2>Welcome to Rindu Boutique</h2>
        <q-carousel
          swipeable
          animated
          v-model="slide"
          :autoplay="autoplay"
          ref="carousel"
          infinite
          control-color="white"
          control-text-color="black"
          arrows
          class="carousel-full-width"
          style="margin-top: 20px; height: 400px;"
        >
          <q-carousel-slide :name="1" img-src="/images/gambar 1.jpg" />
          <q-carousel-slide :name="2" img-src="/images/gambar 2.jpg" />
          <q-carousel-slide :name="3" img-src="/images/gambar 3.jpg" />
          <q-carousel-slide :name="4" img-src="/images/gambar 4.jpg" />
        </q-carousel>
        <p>Discover the latest fashion trends</p>
      </div>
    </div>
    <section class="product-section">
      <div class="container">
        <div class="row">
          <div class="col-md-4 col-sm-6 col-12" v-for="product in products" :key="product.id">
            <div class="product-card">
              <img class="product-image" :src="product.image" :alt="product.name">
              <div class="product-details">
                <h5 class="product-name">{{ product.name }}</h5>
                <p class="product-price">{{ product.price }}</p>
                <button @click="addToCart(product)" class="btn-add-to-cart">Tambahkan Kedalam Keranjang</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="video-section">
      <div class="video-container">
        <q-card class="video-card">
          <q-video src="https://www.youtube.com/embed/afTaOEaYhgc?rel=0" />
          <q-card-section class="video-info">
            <div class="video-title">Rindu Boutique</div>
            <div class="video-author">by Rindu Sakinah</div>
          </q-card-section>
          <q-card-section class="video-description">
            Welcome to Rindu Boutique - Where Style Meets Elegance!
          </q-card-section>
        </q-card>
      </div>
    </section>
    <footer class="footer">
      <div class="container">
        <p>&copy; 2024 Rindu Boutique. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'App',
  setup() {
    const slide = ref(1)
    const autoplay = ref(false)

    return { slide, autoplay }
  },
  data() {
    return {
      products: [
        { id: 1, name: 'Dress 1', image: '/images/gambar 5.jpg', price: 'Rp 120.000,00' },
        { id: 2, name: 'Dress 2', image: '/images/gambar 6.jpg', price: 'Rp 320.000,00' },
        { id: 3, name: 'Dress 3', image: '/images/gambar 7.jpg', price: 'Rp 80.000,00' },
      ]
    }
  },
  methods: {
    addToCart(product) {
      alert('Produk Ditambahkan Kedalam Keranjang: ' + product.name)
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap');

body {
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f9f9f9;
}

.header {
  background-color: #6c63ff;
  color: white;
  padding: 20px 0;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.header-content {
  max-width: 800px;
  margin: 0 auto;
}

.header h1 {
  margin: 0;
  font-size: 2.5rem;
}

.hero-section {
  position: relative;
  height: 600px;
  overflow: hidden;
  text-align: center;
  background: linear-gradient(to bottom, rgba(0,0,0,0.3), rgba(0,0,0,0.7)), url('/images/hero-bg.jpg') no-repeat center center;
  background-size: cover;
}

.hero-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.hero-text h2 {
  font-size: 2rem;
  margin-bottom: 10px;
  animation: fadeIn 2s ease-in-out;
}

.hero-text p {
  font-size: 1.5rem;
}

.carousel-full-width {
  width: 100%;
}

.q-carousel {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.1);
}

.q-carousel-slide img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.product-section {
  padding: 40px 0;
  background: #ffffff;
}

.product-card {
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  padding: 20px;
  text-align: center;
  transition: transform 0.3s ease-in-out;
  cursor: pointer;
}

.product-card:hover {
  transform: translateY(-5px);
}

.product-image {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
}

.product-details {
  margin-top: 10px;
}

.product-name {
  margin: 0;
  font-size: 1.5rem;
}

.product-price {
  margin: 5px 0;
  font-size: 1.2rem;
  color: #6c63ff;
}

.btn-add-to-cart {
  background-color: #6c63ff;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btn-add-to-cart:hover {
  background-color: #514ac3;
}

.video-section {
  margin-top: 40px;
}

.video-container {
  display: flex;
  justify-content: center;
}

.video-card {
  max-width: 800px;
  width: 100%;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  border-radius: 12px;
  overflow: hidden;
  transition: transform 0.3s ease-in-out;
}

.video-card:hover {
  transform: scale(1.02);
}

.video-info {
  background: #6c63ff;
  color: white;
  padding: 10px 20px;
}

.video-title {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 5px;
}

.video-author {
  font-size: 0.9rem;
  color: #d1d1d1;
}

.video-description {
  padding: 15px 20px;
}

.footer {
  background-color: #6c63ff;
  color: white;
  text-align: center;
  padding: 20px 0;
  margin-top: 40px;
}
</style>
