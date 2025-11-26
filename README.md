<! html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ElektroShop - Toko Elektronik Online</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #f5f5f5;
            color: #333;
        }

        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
        }

        .cart-btn {
            background: white;
            color: #667eea;
            border: none;
            padding: 10px 20px;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            position: relative;
            transition: transform 0.2s;
        }

        .cart-btn:hover {
            transform: scale(1.05);
        }

        .cart-count {
            background: #ff4757;
            color: white;
            border-radius: 50%;
            padding: 2px 8px;
            font-size: 0.8rem;
            position: absolute;
            top: -5px;
            right: -5px;
        }

        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 20px;
        }

        .search-bar {
            background: white;
            padding: 1rem;
            border-radius: 10px;
            margin-bottom: 2rem;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .search-bar input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
        }

        .categories {
            display: flex;
            gap: 10px;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .category-btn {
            padding: 10px 20px;
            border: none;
            background: white;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .category-btn:hover, .category-btn.active {
            background: #667eea;
            color: white;
            transform: translateY(-2px);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
            margin-bottom: 3rem;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
        }

        .product-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-name {
            font-size: 1.1rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .product-desc {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        .product-price {
            color: #667eea;
            font-size: 1.3rem;
            font-weight: bold;
            margin-bottom: 1rem;
        }

        .add-to-cart {
            width: 100%;
            padding: 12px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.3s;
        }

        .add-to-cart:hover {
            background: #5568d3;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 200;
            align-items: center;
            justify-content: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            border-radius: 15px;
            padding: 2rem;
            max-width: 600px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .modal-title {
            font-size: 1.5rem;
            font-weight: bold;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: #666;
        }

        .cart-item {
            display: flex;
            gap: 1rem;
            padding: 1rem;
            border-bottom: 1px solid #e0e0e0;
            align-items: center;
        }

        .cart-item-image {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-name {
            font-weight: bold;
            margin-bottom: 0.3rem;
        }

        .cart-item-price {
            color: #667eea;
        }

        .quantity-controls {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        .qty-btn {
            width: 30px;
            height: 30px;
            border: none;
            background: #667eea;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        .remove-btn {
            background: #ff4757;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
        }

        .cart-total {
            margin-top: 1.5rem;
            padding-top: 1rem;
            border-top: 2px solid #e0e0e0;
        }

        .total-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 1rem;
            font-size: 1.2rem;
            font-weight: bold;
        }

        .checkout-btn {
            width: 100%;
            padding: 15px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: bold;
            margin-top: 1rem;
        }

        .checkout-btn:hover {
            background: #5568d3;
        }

        .empty-cart {
            text-align: center;
            padding: 2rem;
            color: #666;
        }

        .checkout-form {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .form-group label {
            font-weight: bold;
        }

        .form-group input, .form-group textarea {
            padding: 10px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
        }

        .success-message {
            background: #2ecc71;
            color: white;
            padding: 1.5rem;
            border-radius: 10px;
            text-align: center;
            margin-bottom: 1rem;
        }
    </style>
</head>
<body>
    <header>
        <div class="header-content">
         aisyah ektroShop</div>
            <button class="cart-btn" onclick="openCart()">
                🛒 Keranjang
                <span class="cart-count" id="cartCount">0</span>
            </button>
        </div>
    </header>

    <div class="container">
        <div class="search-bar">
            <input type="text" id="searchInput" placeholder="Cari produk elektronik..." onkeyup="searchProducts()">
        </div>

        <div class="categories">
            <button class="category-btn active" onclick="filterCategory('semua')">Semua</button>
            <button class="category-btn" onclick="filterCategory('smartphone')">Smartphone</button>
            <button class="category-btn" onclick="filterCategory('laptop')">Laptop</button>
            <button class="category-btn" onclick="filterCategory('audio')">Audio</button>
            <button class="category-btn" onclick="filterCategory('aksesoris')">Aksesoris</button>
        </div>

        <div class="products-grid" id="productsGrid"></div>
    </div>

    <div class="modal" id="cartModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">Keranjang Belanja</div>
                <button class="close-btn" onclick="closeCart()">×</button>
            </div>
            <div id="cartItems"></div>
            <div class="cart-total" id="cartTotal"></div>
        </div>
    </div>

    <div class="modal" id="checkoutModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">Checkout</div>
                <button class="close-btn" onclick="closeCheckout()">×</button>
            </div>
            <div id="checkoutContent"></div>
        </div>
    </div>

    <script>
        const products = [
            {id: 1, name: 'iPhone 15 Pro', category: 'smartphone', price: 18999000, icon: '📱', desc: 'Smartphone flagship dengan chip A17 Pro'},
            {id: 2, name: 'Samsung Galaxy S24', category: 'smartphone', price: 13999000, icon: '📱', desc: 'Smartphone dengan AI terkini'},
            {id: 3, name: 'MacBook Pro M3', category: 'laptop', price: 29999000, icon: '💻', desc: 'Laptop powerful untuk profesional'},
            {id: 4, name: 'ASUS ROG Gaming', category: 'laptop', price: 24999000, icon: '💻', desc: 'Laptop gaming performa tinggi'},
            {id: 5, name: 'Sony WH-1000XM5', category: 'audio', price: 4999000, icon: '🎧', desc: 'Headphone noise cancelling terbaik'},
            {id: 6, name: 'AirPods Pro 2', category: 'audio', price: 3499000, icon: '🎧', desc: 'Earbuds dengan audio spatial'},
            {id: 7, name: 'iPad Pro 12.9"', category: 'tablet', price: 16999000, icon: '📱', desc: 'Tablet profesional dengan M2 chip'},
            {id: 8, name: 'Samsung Smart TV 65"', category: 'tv', price: 12999000, icon: '📺', desc: 'Smart TV 4K QLED'},
            {id: 9, name: 'Power Bank 20000mAh', category: 'aksesoris', price: 299000, icon: '🔋', desc: 'Charger portable fast charging'},
            {id: 10, name: 'Wireless Mouse Gaming', category: 'aksesoris', price: 799000, icon: '🖱️', desc: 'Mouse gaming presisi tinggi'},
            {id: 11, name: 'Mechanical Keyboard RGB', category: 'aksesoris', price: 1299000, icon: '⌨️', desc: 'Keyboard gaming mekanik'},
            {id: 12, name: 'Webcam 4K HD', category: 'aksesoris', price: 1499000, icon: '📷', desc: 'Webcam untuk streaming & meeting'}
        ];

        let cart = [];
        let currentFilter = 'semua';

        function displayProducts(productsToShow = products) {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = productsToShow.map(p => `
                <div class="product-card">
                    <div class="product-image">${p.icon}</div>
                    <div class="product-info">
                        <div class="product-name">${p.name}</div>
                        <div class="product-desc">${p.desc}</div>
                        <div class="product-price">Rp ${p.price.toLocaleString('id-ID')}</div>
                        <button class="add-to-cart" onclick="addToCart(${p.id})">Tambah ke Keranjang</button>
                    </div>
                </div>
            `).join('');
        }

        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existingItem = cart.find(item => item.id === productId);
            
            if (existingItem) {
                existingItem.quantity++;
            } else {
                cart.push({...product, quantity: 1});
            }
            
            updateCartCount();
            showNotification('Produk ditambahkan ke keranjang!');
        }

        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            document.getElementById('cartCount').textContent = count;
        }

        function openCart() {
            displayCart();
            document.getElementById('cartModal').classList.add('active');
        }

        function closeCart() {
            document.getElementById('cartModal').classList.remove('active');
        }

        function displayCart() {
            const cartItemsDiv = document.getElementById('cartItems');
            const cartTotalDiv = document.getElementById('cartTotal');

            if (cart.length === 0) {
                cartItemsDiv.innerHTML = '<div class="empty-cart">Keranjang belanja kosong</div>';
                cartTotalDiv.innerHTML = '';
                return;
            }

            cartItemsDiv.innerHTML = cart.map(item => `
                <div class="cart-item">
                    <div class="cart-item-image">${item.icon}</div>
                    <div class="cart-item-info">
                        <div class="cart-item-name">${item.name}</div>
                        <div class="cart-item-price">Rp ${item.price.toLocaleString('id-ID')}</div>
                    </div>
                    <div class="quantity-controls">
                        <button class="qty-btn" onclick="changeQuantity(${item.id}, -1)">-</button>
                        <span>${item.quantity}</span>
                        <button class="qty-btn" onclick="changeQuantity(${item.id}, 1)">+</button>
                    </div>
                    <button class="remove-btn" onclick="removeFromCart(${item.id})">Hapus</button>
                </div>
            `).join('');

            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            cartTotalDiv.innerHTML = `
                <div class="total-row">
                    <span>Total:</span>
                    <span>Rp ${total.toLocaleString('id-ID')}</span>
                </div>
                <button class="checkout-btn" onclick="proceedToCheckout()">Lanjut ke Pembayaran</button>
            `;
        }

        function changeQuantity(productId, change) {
            const item = cart.find(i => i.id === productId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    updateCartCount();
                    displayCart();
                }
            }
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCartCount();
            displayCart();
        }

        function proceedToCheckout() {
            closeCart();
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            
            document.getElementById('checkoutContent').innerHTML = `
                <form class="checkout-form" onsubmit="completeOrder(event)">
                    <div class="form-group">
                        <label>Nama Lengkap</label>
                        <input type="text" required>
                    </div>
                    <div class="form-group">
                        <label>Email</label>
                        <input type="email" required>
                    </div>
                    <div class="form-group">
                        <label>Nomor Telepon</label>
                        <input type="tel" required>
                    </div>
                    <div class="form-group">
                        <label>Alamat Lengkap</label>
                        <textarea rows="3" required></textarea>
                    </div>
                    <div class="form-group">
                        <label>Metode Pembayaran</label>
                        <select required style="padding: 10px; border: 2px solid #e0e0e0; border-radius: 8px;">
                            <option value="">Pilih metode pembayaran</option>
                            <option value="transfer">Transfer Bank</option>
                            <option value="cod">COD (Cash on Delivery)</option>
                            <option value="ewallet">E-Wallet</option>
                        </select>
                    </div>
                    <div class="total-row">
                        <span>Total Pembayaran:</span>
                        <span>Rp ${total.toLocaleString('id-ID')}</span>
                    </div>
                    <button type="submit" class="checkout-btn">Konfirmasi Pesanan</button>
                </form>
            `;
            
            document.getElementById('checkoutModal').classList.add('active');
        }

        function closeCheckout() {
            document.getElementById('checkoutModal').classList.remove('active');
        }

        function completeOrder(e) {
            e.preventDefault();
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            
            document.getElementById('checkoutContent').innerHTML = `
                <div class="success-message">
                    <h2>✅ Pesanan Berhasil!</h2>
                    <p>Terima kasih atas pembelian Anda</p>
                    <p>Total: Rp ${total.toLocaleString('id-ID')}</p>
                </div>
                <p>Pesanan Anda sedang diproses dan akan segera dikirim. Kami akan mengirimkan konfirmasi melalui email.</p>
                <button class="checkout-btn" onclick="finishOrder()">Selesai</button>
            `;
            
            cart = [];
            updateCartCount();
        }

        function finishOrder() {
            closeCheckout();
        }

        function filterCategory(category) {
            currentFilter = category;
            const buttons = document.querySelectorAll('.category-btn');
            buttons.forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            
            if (category === 'semua') {
                displayProducts(products);
            } else {
                const filtered = products.filter(p => p.category === category);
                displayProducts(filtered);
            }
        }

        function searchProducts() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const filtered = products.filter(p => 
                p.name.toLowerCase().includes(query) || 
                p.desc.toLowerCase().includes(query)
            );
            displayProducts(filtered);
        }

        function showNotification(message) {
            const notif = document.createElement('div');
            notif.style.cssText = 'position: fixed; top: 20px; right: 20px; background: #2ecc71; color: white; padding: 1rem 2rem; border-radius: 8px; z-index: 1000; animation: slideIn 0.3s;';
            notif.textContent = message;
            document.body.appendChild(notif);
            setTimeout(() => notif.remove(), 2000);
        }

        displayProducts();
    </script>
</body>
</html># Toko-elektronik-asiyah
