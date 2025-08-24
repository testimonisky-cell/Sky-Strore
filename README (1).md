<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sky Store — Luxury Black & Gold</title>
<style>
  body { margin:0; font-family:Arial,sans-serif; background:#000; color:#000; scroll-behavior:smooth; }
  .navbar { background:black; color:gold; padding:15px 30px; display:flex; justify-content:space-between; align-items:center; position:sticky; top:0; z-index:1000; }
  .navbar h1 { margin:0; cursor:pointer; color:gold; }
  .navbar a { color:gold; text-decoration:none; font-weight:bold; margin-left:15px; }
  .navbar a:hover { color:#ffcc00; }
  .category-filter { display:flex; justify-content:center; gap:10px; margin:20px 0; flex-wrap:wrap; }
  .category-filter button { padding:8px 16px; border:none; border-radius:6px; cursor:pointer; background:gold; font-weight:bold; transition:0.3s; }
  .category-filter button:hover { background:#ffcc00; }
  .slider-container { position:relative; width:80%; max-width:700px; margin:auto; overflow:hidden; border-radius:12px; margin-bottom:30px; }
  .slides { display:flex; transition:0.5s; }
  .slides img { width:100%; border-radius:12px; }
  .slider button { position:absolute; top:50%; transform:translateY(-50%); background:rgba(0,0,0,0.5); color:white; font-size:20px; padding:10px; border:none; cursor:pointer; border-radius:50%; }
  .prev { left:10px; }
  .next { right:10px; }
  .product-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:20px; padding:20px; }
  .item { background:gold; border-radius:10px; padding:10px; text-align:center; box-shadow:0 4px 12px rgba(0,0,0,0.2); }
  .item img { width:100%; height:250px; object-fit:cover; border-radius:8px; }
  .item h3, .item p { color:black; margin:5px 0; }
  .item button { padding:8px 12px; margin:5px; border:none; border-radius:6px; cursor:pointer; background:black; color:gold; font-weight:bold; }
  .item button:hover { background:#333; }
  #backToTop { position:fixed; bottom:30px; right:30px; padding:10px 15px; background:#ffcc00; color:black; border:none; border-radius:8px; cursor:pointer; display:none; z-index:2000; }
  .cart-popup { position:fixed; top:80px; right:30px; background:white; padding:20px; border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.3); display:none; z-index:2000; max-width:300px; }
  section { padding:50px 20px; max-width:1000px; margin:auto; opacity:0; transform:translateY(50px); transition:0.8s; }
  section.visible { opacity:1; transform:translateY(0); }
  h2.section-title { text-align:center; margin-bottom:30px; font-size:28px; color:#ffcc00; }
  footer { text-align:center; padding:20px; background:black; color:gold; }
</style>
</head>
<body>

<header class="navbar">
  <h1 onclick="window.scrollTo(0,0)">✧Sky Store✧</h1>
  <nav><a href="#" onclick="toggleCart()">🛒 Keranjang</a></nav>
</header>

<div class="category-filter">
  <button onclick="filterCategory('all')">Semua</button>
  <button onclick="filterCategory('Baju')">Baju</button>
  <button onclick="filterCategory('Hoodie')">Hoodie</button>
  <button onclick="filterCategory('Jaket')">Jaket</button>
  <button onclick="filterCategory('Kemeja')">Kemeja</button>
  <button onclick="filterCategory('Sweater')">Sweater</button>
  <button onclick="filterCategory('Celana')">Celana</button>
  <button onclick="filterCategory('Sepatu')">Sepatu</button>
</div>

<div class="slider-container">
  <div class="slides">
    <img src="https://picsum.photos/700/300?random=1" alt="Promo1">
    <img src="https://picsum.photos/700/300?random=2" alt="Promo2">
    <img src="https://picsum.photos/700/300?random=3" alt="Promo3">
  </div>
  <button class="prev" onclick="prevSlide()">‹</button>
  <button class="next" onclick="nextSlide()">›</button>
</div>

<main class="product-grid" id="productGrid">
  <!-- 15 Produk -->
  <div class="item" data-category="Baju">
    <img src="https://picsum.photos/300/400?random=11" alt="Baju 1">
    <h3>Baju Keren 1</h3>
    <p>Rp 120.000</p>
    <button onclick="addToCart('Baju Keren 1',120000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Baju Keren 1',120000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Hoodie">
    <img src="https://picsum.photos/300/400?random=12" alt="Hoodie Stylish">
    <h3>Hoodie Stylish</h3>
    <p>Rp 250.000</p>
    <button onclick="addToCart('Hoodie Stylish',250000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Hoodie Stylish',250000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Jaket">
    <img src="https://picsum.photos/300/400?random=13" alt="Jaket Trendy">
    <h3>Jaket Trendy</h3>
    <p>Rp 300.000</p>
    <button onclick="addToCart('Jaket Trendy',300000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Jaket Trendy',300000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Kemeja">
    <img src="https://picsum.photos/300/400?random=14" alt="Kemeja Casual">
    <h3>Kemeja Casual</h3>
    <p>Rp 180.000</p>
    <button onclick="addToCart('Kemeja Casual',180000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Kemeja Casual',180000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Sweater">
    <img src="https://picsum.photos/300/400?random=15" alt="Sweater Hangat">
    <h3>Sweater Hangat</h3>
    <p>Rp 220.000</p>
    <button onclick="addToCart('Sweater Hangat',220000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Sweater Hangat',220000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Celana">
    <img src="https://picsum.photos/300/400?random=16" alt="Celana Jeans">
    <h3>Celana Jeans</h3>
    <p>Rp 200.000</p>
    <button onclick="addToCart('Celana Jeans',200000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Celana Jeans',200000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Sepatu">
    <img src="https://picsum.photos/300/400?random=17" alt="Sepatu Casual">
    <h3>Sepatu Casual</h3>
    <p>Rp 400.000</p>
    <button onclick="addToCart('Sepatu Casual',400000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Sepatu Casual',400000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Baju">
    <img src="https://picsum.photos/300/400?random=18" alt="Baju 2">
    <h3>Baju Trendy 2</h3>
    <p>Rp 150.000</p>
    <button onclick="addToCart('Baju Trendy 2',150000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Baju Trendy 2',150000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Hoodie">
    <img src="https://picsum.photos/300/400?random=19" alt="Hoodie 2">
    <h3>Hoodie Premium</h3>
    <p>Rp 275.000</p>
    <button onclick="addToCart('Hoodie Premium',275000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Hoodie Premium',275000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Jaket">
    <img src="https://picsum.photos/300/400?random=20" alt="Jaket 2">
    <h3>Jaket Kulit</h3>
    <p>Rp 350.000</p>
    <button onclick="addToCart('Jaket Kulit',350000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Jaket Kulit',350000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Kemeja">
    <img src="https://picsum.photos/300/400?random=21" alt="Kemeja 2">
    <h3>Kemeja Formal</h3>
    <p>Rp 200.000</p>
    <button onclick="addToCart('Kemeja Formal',200000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Kemeja Formal',200000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Sweater">
    <img src="https://picsum.photos/300/400?random=22" alt="Sweater 2">
    <h3>Sweater Rajut</h3>
    <p>Rp 240.000</p>
    <button onclick="addToCart('Sweater Rajut',240000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Sweater Rajut',240000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Celana">
    <img src="https://picsum.photos/300/400?random=23" alt="Celana 2">
    <h3>Celana Chino</h3>
    <p>Rp 210.000</p>
    <button onclick="addToCart('Celana Chino',210000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Celana Chino',210000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Sepatu">
    <img src="https://picsum.photos/300/400?random=24" alt="Sepatu 2">
    <h3>Sepatu Sneakers</h3>
    <p>Rp 420.000</p>
    <button onclick="addToCart('Sepatu Sneakers',420000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('Sepatu Sneakers',420000)">Klik untuk Beli</button>
  </div>
  <div class="item" data-category="Baju">
    <img src="https://picsum.photos/300/400?random=25" alt="Baju 3">
    <h3>T-Shirt Casual</h3>
    <p>Rp 130.000</p>
    <button onclick="addToCart('T-Shirt Casual',130000)">Tambah ke Keranjang</button>
    <button onclick="buyNow('T-Shirt Casual',130000)">Klik untuk Beli</button>
  </div>
</main>

<section class="about">
  <h2 class="section-title">Tentang Sky Store</h2>
  <p>Kami menjual berbagai pakaian stylish untuk semua usia. Sky Store selalu menghadirkan produk berkualitas, harga terjangkau, dan pelayanan cepat.</p>
</section>

<section class="contact">
  <h2 class="section-title">Kontak Kami</h2>
  <form onsubmit="alert('Pesan terkirim!'); return false;">
    <input type="text" placeholder="Nama" required>
    <input type="email" placeholder="Email" required>
    <textarea placeholder="Pesan" rows="4" required></textarea>
    <button type="submit">Kirim</button>
  </form>
</section>

<footer>&copy; 2025 Sky Store | Kontak: 085211069474 | IG: @sky.store</footer>
<button id="backToTop" onclick="window.scrollTo({top:0, behavior:'smooth'})">↑ Atas</button>
<div class="cart-popup" id="cartPopup"></div>

<script>
// ===== KERANJANG =====
let cart = [];
function addToCart(name, price) {
  cart.push({ name, price, qty: 1 });
  alert(name + " ditambahkan ke keranjang!");
  updateCartPopup();
}
function toggleCart() {
  const popup = document.getElementById('cartPopup');
  popup.style.display = popup.style.display === 'block' ? 'none' : 'block';
  updateCartPopup();
}
function updateCartPopup() {
  const popup = document.getElementById('cartPopup');
  if(cart.length===0){ popup.innerHTML='Keranjang kosong'; return; }
  let html='<strong>Keranjang:</strong><br>'; let total=0;
  cart.forEach((item,i)=>{ html+=`${i+1}. ${item.name} - Rp ${item.price}<br>`; total+=item.price*item.qty; });
  html+=`<br><strong>Total: Rp ${total}</strong>`;
  popup.innerHTML=html;
}
function showCart(){
  if(cart.length===0){ alert("Keranjang masih kosong!"); return; }
  let msg="Isi Keranjang:\n"; let total=0;
  cart.forEach((item,i)=>{ msg+=`${i+1}. ${item.name} - Rp ${item.price}\n`; total+=item.price*item.qty; });
  msg+="\nTotal: Rp "+total; alert(msg);
}

// ===== BUY NOW VIA WHATSAPP =====
function buyNow(name, price){
  const phone="6285211069474";
  const message=`Halo, saya ingin membeli ${name} seharga Rp ${price}`;
  window.open(`https://wa.me/${phone}?text=${encodeURIComponent(message)}`,"_blank");
}

// ===== FILTER KATEGORI =====
function filterCategory(category){
  document.querySelectorAll('.item').forEach(p=>{ p.style.display=(category==='all'||p.dataset.category===category)?'block':'none'; });
}

// ===== BACK TO TOP =====
const backBtn=document.getElementById('backToTop');
window.addEventListener('scroll',()=>{ if(backBtn) backBtn.style.display=window.scrollY>300?'block':'none'; });

// ===== SLIDER =====
let slideIndex=0;
const slides=document.querySelector('.slides');
function showSlide(n){ if(!slides) return; if(n>=slides.children.length) slideIndex=0; if(n<0) slideIndex=slides.children.length-1; slides.style.transform=`translateX(${-slideIndex*100}%)`; }
function nextSlide(){ slideIndex++; showSlide(slideIndex); }
function prevSlide(){ slideIndex--; showSlide(slideIndex); }
if(slides) setInterval(()=>{ slideIndex++; showSlide(slideIndex); },5000);

// ===== ANIMASI SECTION SAAT SCROLL =====
document.querySelectorAll('section').forEach(section=>{
  const observer=new IntersectionObserver(entries=>{ entries.forEach(entry=>{ if(entry.isIntersecting) entry.target.classList.add('visible'); }); }, {threshold:0.1});
  observer.observe(section);
});

// ===== FALLBACK GAMBAR =====
document.querySelectorAll('.item img, .slides img').forEach(img=>{ img.onerror=()=>{ img.src='https://via.placeholder.com/300x400?text=No+Image'; }; });
</script>
</body>
</html>
