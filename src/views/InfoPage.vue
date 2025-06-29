<template>
  <div class="sidebar-layout">
    <aside class="sidebar">
      <div class="menu-header" @click="toggleMenu">
        <h2>Menu</h2>
        <span class="menu-toggle-icon">{{ menuOpen ? '▲' : '▼' }}</span>
      </div>
      <transition name="fade-menu">
        <div v-if="menuOpen" class="menu-buttons">
          <router-link to="/" class="menu-btn">Home</router-link>
          <router-link to="/info" class="menu-btn">Computer Products</router-link>
          <router-link to="/contact" class="menu-btn">Contact</router-link>
          <router-link to="/register" class="menu-btn">Register</router-link>
        </div>
      </transition>
    </aside>
    <main class="main-content center-content">
      <div class="info-title">
        <h1>Computer Product Recommendations</h1>
        <b class="info-desc">Discover high-quality computer products for work, study, and entertainment</b>
      </div>
      <div class="product-list">
        <div v-for="product in products" :key="product.id" class="product-card">
          <img :src="product.image" :alt="product.name" class="product-image" />
          <h2 class="product-name">{{ product.name }}</h2>
          <p class="product-desc">{{ product.desc }}</p>
          <div class="product-footer">
            <span class="product-price">฿{{ product.price }}</span>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
export default defineComponent({
  setup() {
    const menuOpen = ref(true);
    const toggleMenu = () => {
      menuOpen.value = !menuOpen.value;
    };
    const products = [
      {
        id: 1,
        name: 'MSI Thin 15 B13VE-1608TH (Cosmos Gray)',
        desc: 'Brand: MSI | Intel Core i5-13420H | RTX 4050 | 16GB RAM | 512GB SSD | 15.6" FHD 144Hz',
        price: 27990,
        image: '/Img/product34669_800.jpg',
      },
      {
        id: 2,
        name: 'Logitech MX Master 3S Wireless Mouse',
        desc: 'Ergonomic wireless mouse with ultra-fast scrolling and customizable buttons.',
        price: 3490,
        image: 'https://resource.logitech.com/w_800,c_limit,q_auto,f_auto,dpr_1.0/d_transparent.gif/content/dam/logitech/en/products/mice/mx-master-3s/gallery/mx-master-3s-top-view-graphite.png',
      },
      {
        id: 3,
        name: 'Dell UltraSharp 27" Monitor U2722D',
        desc: '27-inch QHD IPS display, 100% sRGB, USB-C connectivity, ideal for professionals.',
        price: 13900,
        image: 'https://i.dell.com/sites/csimages/Video_Imagery/all/dell-ultrasharp-u2722d-monitor.png',
      },
    ];
    return { menuOpen, toggleMenu, products };
  }
});
</script>

<style scoped>
.sidebar-layout {
  display: flex;
  height: 100vh;
  background: linear-gradient(135deg, #e3f0ff 0%, #b6c6d6 100%);
  animation: fadeInBg 1.2s;
}
@keyframes fadeInBg {
  from { opacity: 0; }
  to { opacity: 1; }
}
.sidebar {
  width: 220px;
  background: #3a4a5a;
  color: #fff;
  padding: 2rem 1rem;
  min-height: 100vh;
  box-shadow: 4px 0 24px #0002;
  z-index: 2;
}
.menu-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  user-select: none;
  margin-bottom: 0.5rem;
  padding: 0.2rem 0.5rem 0.2rem 0;
}
.menu-header h2 {
  color: #b6e0ff;
  font-size: 1.3rem;
  margin: 0;
  letter-spacing: 1px;
  text-shadow: 0 2px 8px #0002;
}
.menu-toggle-icon {
  font-size: 1.2rem;
  color: #3880ff;
  margin-left: 0.5rem;
  transition: transform 0.2s;
}
.menu-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
}
.menu-btn {
  display: block;
  padding: 0.7rem 1.2rem;
  background: linear-gradient(90deg, #6cb6ff 60%, #b6c6d6 100%);
  color: #234;
  border: none;
  border-radius: 8px;
  font-size: 1.08rem;
  font-weight: 500;
  text-align: center;
  text-decoration: none;
  transition: background 0.2s, box-shadow 0.2s, transform 0.15s, color 0.2s;
  box-shadow: 0 2px 12px #6cb6ff22;
  cursor: pointer;
  outline: none;
}
.menu-btn:hover, .menu-btn.router-link-active {
  background: linear-gradient(90deg, #3a4a5a 60%, #6cb6ff 100%);
  color: #fff;
  box-shadow: 0 4px 24px #6cb6ff55;
  transform: translateY(-2px) scale(1.04);
}
.main-content {
  flex: 1;
  background: transparent;
  padding: 2rem 0;
  overflow-y: auto;
}
.center-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}
.info-title {
  background: rgba(58,74,90,0.98);
  padding: 1.5rem 2.2rem 1.2rem 2.2rem;
  border-radius: 24px;
  box-shadow: 0 8px 32px #6cb6ff44;
  min-width: 350px;
  max-width: 90vw;
  text-align: center;
  border: 2px solid #b6e0ff;
  margin-bottom: 2rem;
  animation: popIn 0.8s cubic-bezier(.68,-0.55,.27,1.55);
}
.info-title h1 {
  color: #b6e0ff;
  font-size: 2.1rem;
  font-weight: bold;
  margin-bottom: 0.7rem;
  letter-spacing: 1px;
  text-shadow: 0 2px 8px #0002;
}
.info-desc {
  font-size: 1.1rem;
  color: #fff;
  display: block;
}
.product-list {
  display: flex;
  flex-wrap: wrap;
  gap: 2.5rem 2rem; /* เพิ่มช่องว่างระหว่างสินค้า */
  justify-content: center;
  width: 100%;
}
.product-card {
  background: #fff;
  border-radius: 18px;
  box-shadow: 0 4px 24px #6cb6ff33;
  padding: 1.5rem 1.2rem 1.2rem 1.2rem;
  width: 300px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid #b6e0ff;
  transition: box-shadow 0.2s, transform 0.15s;
  position: relative;
  margin-bottom: 1.5rem; /* เพิ่มช่องว่างด้านล่างแต่ละการ์ด */
}
.product-card:hover {
  box-shadow: 0 8px 32px #6cb6ff55;
  transform: translateY(-4px) scale(1.03);
  border-color: #6cb6ff;
}
.product-image {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-radius: 12px;
  margin-bottom: 1.2rem; /* เพิ่มช่องว่างด้านล่างรูปภาพ */
  border: 1.5px solid #b6e0ff;
}
.product-name {
  font-size: 1.25rem;
  color: #234;
  font-weight: bold;
  margin-bottom: 0.5rem;
}
.product-desc {
  color: #444;
  font-size: 1rem;
  margin-bottom: 1rem;
  text-align: center;
}
.product-footer {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  width: 100%;
}
.product-price {
  color: #3a4a5a;
  font-size: 1.1rem;
  font-weight: bold;
}
.fade-menu-enter-active, .fade-menu-leave-active {
  transition: opacity 0.25s;
}
.fade-menu-enter-from, .fade-menu-leave-to {
  opacity: 0;
}
</style>