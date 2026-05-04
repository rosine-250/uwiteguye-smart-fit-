<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Uwiteguye Smart Fit | Shop Your Perfect Size</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #27ae60;
            --dark: #333333;
        }
        body {
            font-family: 'Segoe UI', ATahoma, Geneva, Verdana, sans-serif;
            color: var(--dark);
            background-color: #ffffff;
            margin: 0;
            scroll-behavior: smooth;
        }
        .bg-primary { background-color: var(--primary); }
        .text-primary { color: var(--primary); }

        /* Hero Slider */
        .hero-section {
            position: relative;
            height: 80vh;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-align: center;
        }
        .hero-slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            opacity: 0;
            transition: opacity 1.5s ease-in-out;
            z-index: 1;
        }
        .hero-slide.active { opacity: 1; }
        .hero-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 2;
        }
        .hero-content {
            position: relative;
            z-index: 3;
            max-width: 800px;
            padding: 20px;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .cart-sidebar {
            position: fixed;
            top: 0;
            right: 0;
            height: 100%;
            width: 100%;
            max-width: 400px;
            background: white;
            box-shadow: -5px 0 15px rgba(0,0,0,0.1);
            transform: translateX(100%);
            transition: transform 0.3s ease-in-out;
            z-index: 1100;
        }
        .cart-sidebar.open { transform: translateX(0); }

        .size-btn.active {
            background-color: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        .social-float {
            transition: all 0.3s ease;
        }
        .social-float:hover {
            transform: translateY(-5px);
        }
    </style>
</head>
<body>

    <!-- Navigation -->
    <nav class="sticky top-0 bg-white shadow-md z-50">
        <div class="container mx-auto px-4 py-4 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <div class="w-10 h-10 bg-primary rounded-lg flex items-center justify-center text-white font-bold text-xl shadow-lg">U</div>
                <span class="text-xl font-black tracking-tight">UWITEGUYE <span class="text-primary uppercase font-light">Smart Fit</span></span>
            </div>
            <div class="flex items-center space-x-4">
                <div class="hidden md:flex items-center space-x-4 mr-4 border-r pr-4">
                    <a href="https://instagram.com/rosin-e26" target="_blank" class="text-gray-500 hover:text-pink-600 transition"><i class="fab fa-instagram"></i></a>
                    <a href="https://facebook.com/U.RO-SI-NE" target="_blank" class="text-gray-500 hover:text-blue-700 transition"><i class="fab fa-facebook"></i></a>
                    <a href="https://wa.me/250795063156" target="_blank" class="text-gray-500 hover:text-green-600 transition"><i class="fab fa-whatsapp"></i></a>
                </div>
                <button onclick="toggleCart()" class="relative p-2 bg-gray-100 rounded-full hover:bg-primary hover:text-white transition">
                    <i class="fas fa-shopping-bag text-lg"></i>
                    <span id="cart-count" class="absolute -top-1 -right-1 bg-red-500 text-white text-[10px] rounded-full h-5 w-5 flex items-center justify-center border-2 border-white">0</span>
                </button>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <div class="hero-section">
        <div class="hero-slide active" style="background-image: url('https://images.unsplash.com/photo-1490481651871-ab68de25d43d?q=80&w=2070');"></div>
        <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1441984904996-e0b6ba687e04?q=80&w=2070');"></div>
        <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1470309864661-68328b2cd0a5?q=80&w=2070');"></div>
        <div class="hero-overlay"></div>
        
        <div class="hero-content">
            <h1 class="text-5xl md:text-7xl font-bold mb-4 uppercase tracking-tighter">Get The Perfect Fit</h1>
            <p class="text-xl mb-8 font-medium">We deliver clothes to your door and provide a mobile fitting room so you can try them on before you pay!</p>
            <div class="flex flex-col sm:flex-row justify-center gap-4">
                <a href="#size-tool" class="bg-primary px-10 py-4 rounded-full font-bold text-lg hover:bg-green-600 transition shadow-xl">Check My Size</a>
                <a href="#shop" class="bg-white text-black px-10 py-4 rounded-full font-bold text-lg hover:bg-gray-100 transition shadow-xl flex items-center justify-center">Shop Now</a>
            </div>
        </div>
    </div>

    <!-- Size Calculator Section -->
    <section id="size-tool" class="py-20 bg-green-50">
        <div class="container mx-auto px-4 max-w-3xl">
            <div class="bg-white p-10 rounded-[40px] shadow-2xl border-4 border-white">
                <div class="text-center mb-10">
                    <span class="text-primary font-black uppercase text-xs tracking-[0.3em]">Smart Tool</span>
                    <h2 class="text-3xl font-black uppercase tracking-tighter mt-2">Find Your Perfect Size</h2>
                    <p class="text-gray-500 mt-2">Enter your measurements and we will tell you the best fit for you.</p>
                </div>
                
                <div class="grid md:grid-cols-2 gap-6 mb-8">
                    <div class="space-y-2">
                        <label class="text-xs font-black uppercase text-gray-400 ml-2">Height (CM)</label>
                        <input type="number" id="user-height" placeholder="e.g. 175" class="w-full p-5 bg-gray-50 rounded-2xl outline-none border-2 border-transparent focus:border-primary transition font-bold">
                    </div>
                    <div class="space-y-2">
                        <label class="text-xs font-black uppercase text-gray-400 ml-2">Weight (KG)</label>
                        <input type="number" id="user-weight" placeholder="e.g. 70" class="w-full p-5 bg-gray-50 rounded-2xl outline-none border-2 border-transparent focus:border-primary transition font-bold">
                    </div>
                </div>
                
                <button onclick="calculateSize()" class="w-full bg-primary text-white py-5 rounded-2xl font-black uppercase tracking-widest hover:scale-105 transition shadow-lg">Calculate My Size</button>
                
                <div id="size-result" class="mt-10 hidden text-center p-8 bg-gray-900 text-white rounded-3xl animate-pulse">
                    <p class="text-xs font-bold uppercase tracking-widest text-gray-400 mb-2">Our Recommendation:</p>
                    <h3 class="text-5xl font-black text-primary">SIZE <span id="recommended-size">M</span></h3>
                    <p class="mt-4 text-sm text-gray-400 italic">"Based on your body type, this size will fit you comfortably."</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Catalog -->
    <section id="shop" class="py-20">
        <div class="container mx-auto px-4">
            <div class="text-center mb-16">
                <h2 class="text-4xl font-black mb-4 uppercase tracking-tighter">Our New Collection</h2>
                <div class="w-20 h-1 bg-primary mx-auto rounded-full"></div>
            </div>
            <div id="product-list" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-10">
                <!-- Products loaded via JavaScript -->
            </div>
        </div>
    </section>

    <!-- Product Details Modal -->
    <div id="product-modal" class="modal">
        <div class="bg-white rounded-[40px] max-w-4xl w-full mx-4 flex flex-col md:flex-row overflow-hidden relative shadow-2xl">
            <button onclick="closeModal('product-modal')" class="absolute top-6 right-6 w-10 h-10 bg-gray-100 rounded-full flex items-center justify-center hover:bg-black hover:text-white transition z-10">&times;</button>
            <div class="md:w-1/2">
                <img id="modal-img" src="" class="w-full h-full object-cover min-h-[400px]">
            </div>
            <div class="md:w-1/2 p-10 flex flex-col">
                <h2 id="modal-name" class="text-3xl font-black mb-2 uppercase tracking-tight">Product Name</h2>
                <p id="modal-price" class="text-primary text-3xl font-black mb-6">0 RWF</p>
                
                <div class="bg-gray-50 p-6 rounded-2xl mb-8 border-l-4 border-primary">
                    <p class="text-xs font-bold text-gray-400 uppercase mb-2">Expert Note:</p>
                    <p class="text-gray-600 font-medium italic">"This high-quality item is selected by Rosine to make you look stylish and comfortable."</p>
                </div>
                
                <div class="mb-10">
                    <div class="flex justify-between items-center mb-4">
                        <span class="block font-black text-xs uppercase text-gray-400 tracking-widest">Select Your Size:</span>
                        <a href="#size-tool" onclick="closeModal('product-modal')" class="text-[10px] text-primary font-bold underline">Size Guide</a>
                    </div>
                    <div class="flex space-x-3">
                        <button onclick="selectSize('S', this)" id="btn-S" class="size-btn w-14 h-14 border-2 rounded-2xl font-black flex items-center justify-center hover:border-primary transition text-sm">S</button>
                        <button onclick="selectSize('M', this)" id="btn-M" class="size-btn w-14 h-14 border-2 rounded-2xl font-black flex items-center justify-center hover:border-primary transition text-sm">M</button>
                        <button onclick="selectSize('L', this)" id="btn-L" class="size-btn w-14 h-14 border-2 rounded-2xl font-black flex items-center justify-center hover:border-primary transition text-sm">L</button>
                        <button onclick="selectSize('XL', this)" id="btn-XL" class="size-btn w-14 h-14 border-2 rounded-2xl font-black flex items-center justify-center hover:border-primary transition text-sm">XL</button>
                    </div>
                    <p id="size-error" class="text-red-500 text-[10px] mt-4 hidden font-black uppercase"><i class="fas fa-exclamation-circle mr-1"></i> Please choose a size!</p>
                </div>
                
                <button onclick="addToBag()" class="w-full bg-primary text-white py-5 rounded-2xl font-black text-lg hover:bg-green-600 transition shadow-xl mt-auto uppercase tracking-widest">Add to Bag & Order</button>
            </div>
        </div>
    </div>

    <!-- Cart Sidebar -->
    <div id="cart-sidebar" class="cart-sidebar flex flex-col">
        <div class="p-8 border-b flex justify-between items-center bg-gray-50">
            <h2 class="text-2xl font-black uppercase tracking-tighter text-gray-900">Your Bag</h2>
            <button onclick="toggleCart()" class="text-3xl text-gray-300 hover:text-black">&times;</button>
        </div>
        <div id="cart-items" class="flex-grow overflow-y-auto p-8 space-y-6">
            <!-- Items added here -->
        </div>
        <div class="p-8 border-t bg-white">
            <div class="flex justify-between font-black text-xl mb-8">
                <span class="text-gray-400 uppercase text-xs tracking-widest">Total:</span>
                <span id="cart-total" class="text-primary text-2xl">0 RWF</span>
            </div>
            <button onclick="openCheckout()" class="w-full bg-black text-white py-5 rounded-2xl font-black text-lg hover:bg-gray-800 transition shadow-xl uppercase tracking-widest">Place Order Now</button>
        </div>
    </div>

    <!-- Checkout Modal -->
    <div id="checkout-modal" class="modal">
        <div class="bg-white rounded-[40px] max-w-lg w-full p-12 relative mx-4 shadow-2xl">
            <button onclick="closeModal('checkout-modal')" class="absolute top-6 right-6 text-3xl text-gray-300 hover:text-black">&times;</button>
            <div class="text-center mb-10">
                <h2 class="text-3xl font-black mb-2 uppercase tracking-tighter">Shipping Info</h2>
                <p class="text-gray-500 font-medium">We need your contact details for delivery.</p>
            </div>
            <form onsubmit="finishOrder(event)" class="space-y-5">
                <input type="text" id="cust-name" placeholder="Full Name" required class="w-full p-5 bg-gray-50 rounded-2xl outline-none font-bold">
                <input type="tel" id="cust-phone" placeholder="Phone (WhatsApp)" required class="w-full p-5 bg-gray-50 rounded-2xl outline-none font-bold">
                <input type="text" id="cust-loc" placeholder="Location (e.g. Kimironko)" required class="w-full p-5 bg-gray-50 rounded-2xl outline-none font-bold">
                <button type="submit" class="w-full bg-primary text-white py-6 rounded-2xl font-black text-xl mt-6 uppercase tracking-widest">Confirm My Order</button>
            </form>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-950 text-white py-20 text-center relative">
        <div class="container mx-auto px-4">
            <div class="flex items-center justify-center space-x-2 mb-8">
                <div class="w-8 h-8 bg-primary rounded-lg"></div>
                <span class="text-2xl font-black tracking-tighter">UWITEGUYE SMART FIT</span>
            </div>
            <div class="flex justify-center space-x-10 mb-12">
                <a href="https://instagram.com/rosin-e26" target="_blank" class="text-gray-500 hover:text-primary transition text-3xl"><i class="fab fa-instagram"></i></a>
                <a href="https://facebook.com/U.RO-SI-NE" target="_blank" class="text-gray-500 hover:text-primary transition text-3xl"><i class="fab fa-facebook"></i></a>
                <a href="https://wa.me/250795063156" target="_blank" class="text-gray-500 hover:text-primary transition text-3xl"><i class="fab fa-whatsapp"></i></a>
            </div>
            <div class="text-gray-600 text-[10px] uppercase font-black tracking-[0.5em]">
                <p>&copy; 2026 UWITEGUYE SMART FIT</p>
                <p class="text-primary/50 mt-2">Created on: 4 / 5 / 2026</p>
            </div>
        </div>
    </footer>

    <!-- Fixed WhatsApp -->
    <a href="https://wa.me/250795063156" target="_blank" class="fixed bottom-6 right-6 z-[60] bg-green-500 text-white w-16 h-16 rounded-full flex items-center justify-center text-3xl shadow-2xl hover:scale-110 transition">
        <i class="fab fa-whatsapp"></i>
    </a>

    <script>
        const products = [
            { id: 1, name: "Premium White Shirt", price: 22000, img: "https://images.unsplash.com/photo-1598033129183-c4f50c7176c8?q=80&w=800" },
            { id: 2, name: "Summer Floral Dress", price: 25000, img: "https://images.unsplash.com/photo-1515372039744-b8f02a3ae446?q=80&w=800" },
            { id: 3, name: "Urban Street Jacket", price: 38000, img: "https://images.unsplash.com/photo-1551028711-031c50728753?q=80&w=800" },
            { id: 4, name: "Elegant Evening Gown", price: 45000, img: "https://images.unsplash.com/photo-1566174053879-31528523f8ae?q=80&w=800" },
            { id: 5, name: "Classic Men's Suit", price: 65000, img: "https://images.unsplash.com/photo-1593032465175-481ac7f401a0?q=80&w=800" },
            { id: 6, name: "Casual Party Dress", price: 32000, img: "https://images.unsplash.com/photo-1496747611176-843222e1e57c?q=80&w=800" },
            { id: 7, name: "Designer Polo Shirt", price: 18000, img: "https://images.unsplash.com/photo-1586363104862-3a5e2ab60d99?q=80&w=800" },
            { id: 8, name: "Classic Heels", price: 28000, img: "https://images.unsplash.com/photo-1543163521-1bf539c55dd2?q=80&w=800" }
        ];

        let cart = [];
        let currentItem = null;
        let selectedSize = null;
        let recommended = null;

        // Background Slider
        let currentSlide = 0;
        const slides = document.querySelectorAll('.hero-slide');
        function nextSlide() {
            slides[currentSlide].classList.remove('active');
            currentSlide = (currentSlide + 1) % slides.length;
            slides[currentSlide].classList.add('active');
        }
        setInterval(nextSlide, 5000);

        // Size Calculator Logic
        function calculateSize() {
            const h = document.getElementById('user-height').value;
            const w = document.getElementById('user-weight').value;
            const resDiv = document.getElementById('size-result');
            const resSpan = document.getElementById('recommended-size');

            if (!h || !w) return;

            let size = "M";
            // Simple logic for size estimation
            const score = parseInt(w) + (parseInt(h) / 2);
            if (score < 140) size = "S";
            else if (score < 160) size = "M";
            else if (score < 185) size = "L";
            else size = "XL";

            recommended = size;
            resSpan.innerText = size;
            resDiv.classList.remove('hidden');
            
            // Auto-scroll to result
            resDiv.scrollIntoView({ behavior: 'smooth', block: 'center' });
        }

        function loadProducts() {
            const list = document.getElementById('product-list');
            list.innerHTML = products.map(p => `
                <div class="bg-white rounded-[35px] shadow-sm hover:shadow-2xl transition-all duration-500 cursor-pointer overflow-hidden border border-gray-100 group" onclick="openDetails(${p.id})">
                    <div class="relative overflow-hidden h-[350px]">
                        <img src="${p.img}" class="w-full h-full object-cover group-hover:scale-110 transition duration-700">
                    </div>
                    <div class="p-8 text-center">
                        <h3 class="font-black text-lg uppercase tracking-tight mb-2">${p.name}</h3>
                        <p class="text-primary font-black text-xl">${p.price.toLocaleString()} RWF</p>
                        <button class="w-full mt-6 py-4 bg-gray-50 border-2 border-transparent text-gray-900 rounded-2xl font-black uppercase text-[10px] tracking-widest group-hover:border-primary group-hover:bg-white transition">Order Now</button>
                    </div>
                </div>
            `).join('');
        }

        function openDetails(id) {
            const p = products.find(x => x.id === id);
            currentItem = p;
            selectedSize = null;
            document.getElementById('modal-img').src = p.img;
            document.getElementById('modal-name').innerText = p.name;
            document.getElementById('modal-price').innerText = p.price.toLocaleString() + " RWF";
            document.querySelectorAll('.size-btn').forEach(b => b.classList.remove('active'));
            document.getElementById('size-error').classList.add('hidden');
            
            // Highlight recommended size if available
            if (recommended) {
                const btn = document.getElementById('btn-' + recommended);
                if (btn) {
                    btn.classList.add('ring-4', 'ring-primary/20', 'border-primary');
                    selectedSize = recommended;
                    btn.classList.add('active');
                }
            }

            document.getElementById('product-modal').style.display = 'flex';
        }

        function selectSize(size, el) {
            selectedSize = size;
            document.querySelectorAll('.size-btn').forEach(b => {
                b.classList.remove('active', 'ring-4', 'ring-primary/20', 'border-primary');
            });
            el.classList.add('active');
            document.getElementById('size-error').classList.add('hidden');
        }

        function addToBag() {
            if (!selectedSize) {
                document.getElementById('size-error').classList.remove('hidden');
                return;
            }
            cart.push({ ...currentItem, size: selectedSize, cartId: Date.now() });
            updateCart();
            closeModal('product-modal');
            toggleCart();
        }

        function updateCart() {
            document.getElementById('cart-count').innerText = cart.length;
            const itemsDiv = document.getElementById('cart-items');
            const totalDiv = document.getElementById('cart-total');
            
            if (cart.length === 0) {
                itemsDiv.innerHTML = '<div class="text-center py-20 text-gray-300 font-bold uppercase text-xs">Bag is empty</div>';
                totalDiv.innerText = "0 RWF";
                return;
            }

            let total = 0;
            itemsDiv.innerHTML = cart.map((item, index) => {
                total += item.price;
                return `
                    <div class="flex items-center justify-between bg-gray-50 p-4 rounded-2xl">
                        <div class="flex items-center space-x-4">
                            <img src="${item.img}" class="w-12 h-16 object-cover rounded-lg">
                            <div>
                                <p class="font-black text-[10px] uppercase">${item.name}</p>
                                <p class="text-primary font-black text-xs">${item.price.toLocaleString()} RWF</p>
                                <span class="text-[9px] bg-white px-2 py-0.5 rounded font-bold border">SIZE: ${item.size}</span>
                            </div>
                        </div>
                        <button onclick="removeFromCart(${index})" class="text-red-400 hover:text-red-600"><i class="fas fa-trash-alt"></i></button>
                    </div>
                `;
            }).join('');
            totalDiv.innerText = total.toLocaleString() + " RWF";
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            updateCart();
        }

        function toggleCart() {
            document.getElementById('cart-sidebar').classList.toggle('open');
        }

        function openCheckout() {
            if (cart.length === 0) return;
            toggleCart();
            document.getElementById('checkout-modal').style.display = 'flex';
        }

        function closeModal(id) {
            document.getElementById(id).style.display = 'none';
        }

        // Send Order directly to Rosine's WhatsApp
        function finishOrder(e) {
            e.preventDefault();
            const name = document.getElementById('cust-name').value;
            const phone = document.getElementById('cust-phone').value;
            const location = document.getElementById('cust-loc').value;
            
            // Build the WhatsApp message
            let itemsString = "";
            let total = 0;
            cart.forEach(item => {
                itemsString += `- ${item.name} (Size: ${item.size}) - ${item.price.toLocaleString()} RWF\n`;
                total += item.price;
            });

            const message = `*NEW ORDER FROM UWITEGUYE SMART FIT*%0A%0A` +
                            `*Customer:* ${name}%0A` +
                            `*Phone:* ${phone}%0A` +
                            `*Location:* ${location}%0A%0A` +
                            `*Items:*%0A${encodeURIComponent(itemsString)}%0A` +
                            `*Total Price:* ${total.toLocaleString()} RWF%0A%0A` +
                            `Please prepare my items and the Mobile Fitting Room!`;

            // Your WhatsApp Number
            const waNumber = "250795063156";
            
            // Open WhatsApp
            window.open(`https://wa.me/${waNumber}?text=${message}`, '_blank');

            // Show success message on screen
            document.getElementById('checkout-modal').innerHTML = `
                <div class="text-center py-16 px-4">
                    <div class="w-20 h-20 bg-primary text-white rounded-full flex items-center justify-center text-3xl mx-auto mb-6 shadow-xl"><i class="fas fa-check"></i></div>
                    <h2 class="text-2xl font-black mb-4 uppercase tracking-tighter">Order Sent!</h2>
                    <p class="text-gray-500 font-medium text-sm">Thanks <b>${name}</b>. Your order details have been sent to Rosine's WhatsApp. We will call you soon!</p>
                    <button onclick="window.location.reload()" class="mt-10 bg-black text-white px-10 py-4 rounded-2xl font-black uppercase text-xs tracking-widest shadow-xl">Back to Shop</button>
                </div>
            `;
            
            cart = [];
            updateCart();
        }

        window.onload = loadProducts;
    </script>
</body>
</html>
