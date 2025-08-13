# cartzilla
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>Cartzilla - Online Shopping Marketplace</title>
    <style>
        /* Global Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Amazon Ember', Arial, sans-serif;
        }
        
        body {
            background-color: #f3f3f3;
            color: #0F1111;
        }
        
        a {
            text-decoration: none;
            color: inherit;
        }
        
        /* Header Styles */
        header {
            background-color: #131921;
            color: white;
            padding: 15px 20px;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-top {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .logo {
            font-size: 24px;
            font-weight: bold;
            color: #FF9900;
            margin-right: 20px;
        }
        
        .search-bar {
            flex-grow: 1;
            display: flex;
            margin-right: 20px;
        }
        
        .search-bar input {
            width: 100%;
            padding: 10px;
            border: none;
            border-radius: 4px 0 0 4px;
            font-size: 14px;
        }
        
        .search-bar button {
            background-color: #FEBD69;
            border: none;
            padding: 10px 15px;
            border-radius: 0 4px 4px 0;
            cursor: pointer;
        }
        
        .header-actions {
            display: flex;
            align-items: center;
        }
        
        .header-action {
            margin-left: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
        }
        
        .header-action span:first-child {
            font-size: 12px;
        }
        
        .header-action span:last-child {
            font-size: 14px;
            font-weight: bold;
        }
        
        .cart {
            position: relative;
        }
        
        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background-color: #FF9900;
            color: black;
            border-radius: 50%;
            width: 18px;
            height: 18px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            font-weight: bold;
        }
        
        /* Navigation */
        nav {
            background-color: #232F3E;
            padding: 10px 20px;
            display: flex;
            align-items: center;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin-right: 15px;
            font-size: 14px;
            cursor: pointer;
        }
        
        /* Hero Banner */
        .hero {
            height: 300px;
            background-image: url('https://images.unsplash.com/photo-1505740420928-5e560c06d30e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80');
            background-size: cover;
            background-position: center;
            margin-bottom: 20px;
        }
        
        /* Product Grid */
        .products-section {
            padding: 20px;
        }
        
        .section-title {
            font-size: 20px;
            margin-bottom: 15px;
            font-weight: bold;
        }
        
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .product-card {
            background-color: white;
            border-radius: 4px;
            padding: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: transform 0.2s;
        }
        
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .product-image {
            height: 200px;
            background-color: #f7f7f7;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .product-image img {
            max-height: 100%;
            max-width: 100%;
            object-fit: contain;
        }
        
        .product-title {
            font-size: 16px;
            margin-bottom: 10px;
            height: 40px;
            overflow: hidden;
        }
        
        .product-price {
            font-size: 18px;
            font-weight: bold;
            color: #B12704;
            margin-bottom: 10px;
        }
        
        .product-rating {
            color: #FFA41C;
            margin-bottom: 10px;
        }
        
        .product-variants {
            font-size: 12px;
            color: #565959;
            margin-bottom: 10px;
        }
        
        .add-to-cart {
            background-color: #FFD814;
            border: none;
            padding: 8px 15px;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 14px;
        }
        
        .add-to-cart:hover {
            background-color: #F7CA00;
        }
        
        /* Footer */
        footer {
            background-color: #232F3E;
            color: white;
            padding: 30px 20px;
            margin-top: 30px;
        }
        
        .footer-links {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .footer-column h3 {
            font-size: 16px;
            margin-bottom: 10px;
        }
        
        .footer-column ul {
            list-style: none;
        }
        
        .footer-column li {
            margin-bottom: 8px;
            font-size: 14px;
            color: #DDD;
            cursor: pointer;
        }
        
        .footer-bottom {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid #3a4553;
            font-size: 12px;
        }
        
        /* Cart Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 200;
        }
        
        .modal-content {
            background-color: white;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding: 20px;
            width: 80%;
            max-width: 800px;
            max-height: 80vh;
            overflow-y: auto;
            border-radius: 4px;
        }
        
        .close-modal {
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 24px;
            cursor: pointer;
        }
        
        .cart-items {
            margin-top: 20px;
        }
        
        .cart-item {
            display: flex;
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #EEE;
        }
        
        .cart-item-image {
            width: 80px;
            height: 80px;
            margin-right: 15px;
            background-color: #f7f7f7;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .cart-item-image img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }
        
        .cart-item-details {
            flex-grow: 1;
        }
        
        .cart-item-title {
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .cart-item-price {
            color: #B12704;
            margin-bottom: 5px;
        }
        
        .cart-item-quantity {
            display: flex;
            align-items: center;
        }
        
        .quantity-btn {
            width: 25px;
            height: 25px;
            background-color: #F0F2F2;
            border: 1px solid #D5D9D9;
            cursor: pointer;
        }
        
        .quantity-input {
            width: 40px;
            height: 25px;
            text-align: center;
            border: 1px solid #D5D9D9;
            margin: 0 5px;
        }
        
        .remove-item {
            color: #0066C0;
            font-size: 12px;
            cursor: pointer;
        }
        
        .cart-total {
            margin-top: 20px;
            text-align: right;
            font-size: 18px;
            font-weight: bold;
        }
        
        .checkout-btn {
            background-color: #FFA41C;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 15px;
            float: right;
        }
        
        .checkout-btn:hover {
            background-color: #FA8900;
        }

        /* Search results */
        .search-results {
            padding: 20px;
            background-color: white;
            margin: 20px;
            border-radius: 4px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .no-results {
            text-align: center;
            padding: 40px;
            font-size: 18px;
            color: #555;
        }

        /* Category tabs */
        .category-tabs {
            display: flex;
            overflow-x: auto;
            padding: 10px 20px;
            background-color: white;
            margin-bottom: 20px;
        }

        .category-tab {
            padding: 8px 16px;
            margin-right: 10px;
            white-space: nowrap;
            cursor: pointer;
            border-radius: 4px;
        }

        .category-tab.active {
            background-color: #FFD814;
            font-weight: bold;
        }

        /* Variant selector */
        .variant-selector {
            margin-bottom: 10px;
        }

        .variant-options {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
            margin-top: 5px;
        }

        .variant-option {
            padding: 3px 8px;
            border: 1px solid #D5D9D9;
            border-radius: 4px;
            font-size: 12px;
            cursor: pointer;
        }

        .variant-option.selected {
            background-color: #FFD814;
            border-color: #F7CA00;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-top">
            <div class="logo">Cartzilla</div>
            <div class="search-bar">
                <input type="text" id="search-input" placeholder="Search for products...">
                <button id="search-button">Search</button>
            </div>
            <div class="header-actions">
                <div class="header-action">
                    <span>Hello, Sign in</span>
                    <span>Account & Lists</span>
                </div>
                <div class="header-action">
                    <span>Returns</span>
                    <span>& Orders</span>
                </div>
                <div class="header-action cart" onclick="openCart()">
                    <span id="cart-total-items">Cart</span>
                    <div class="cart-count" id="cart-count">0</div>
                </div>
            </div>
        </div>
        <nav>
            <ul class="nav-links">
                <li>All</li>
                <li>Today's Deals</li>
                <li>Customer Service</li>
                <li>Registry</li>
                <li>Gift Cards</li>
                <li>Sell</li>
            </ul>
        </nav>
    </header>

    <!-- Hero Banner -->
    <div class="hero"></div>

    <!-- Category Tabs -->
    <div class="category-tabs" id="category-tabs">
        <!-- Categories will be added dynamically -->
    </div>

    <!-- Main Content -->
    <div id="main-content">
        <!-- Product Sections -->
        <div class="products-section">
            <h2 class="section-title">Featured Products</h2>
            <div class="product-grid" id="featured-grid">
                <!-- Product cards will be added dynamically with JavaScript -->
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="footer-links">
            <div class="footer-column">
                <h3>Get to Know Us</h3>
                <ul>
                    <li>About Us</li>
                    <li>Careers</li>
                    <li>Press Releases</li>
                    <li>Cartzilla Science</li>
                </ul>
            </div>
            <div class="footer-column">
                <h3>Make Money with Us</h3>
                <ul>
                    <li>Sell products on Cartzilla</li>
                    <li>Sell on Cartzilla Business</li>
                    <li>Become an Affiliate</li>
                    <li>Advertise Your Products</li>
                </ul>
            </div>
            <div class="footer-column">
                <h3>Payment Products</h3>
                <ul>
                    <li>Cartzilla Business Card</li>
                    <li>Shop with Points</li>
                    <li>Reload Your Balance</li>
                    <li>Cartzilla Currency Converter</li>
                </ul>
            </div>
            <div class="footer-column">
                <h3>Let Us Help You</h3>
                <ul>
                    <li>Your Account</li>
                    <li>Your Orders</li>
                    <li>Shipping Rates & Policies</li>
                    <li>Returns & Replacements</li>
                    <li>Help</li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">
            <p>© 2023 Cartzilla.com, Inc. or its affiliates</p>
        </div>
    </footer>

    <!-- Shopping Cart Modal -->
    <div class="modal" id="cart-modal">
        <div class="modal-content">
            <span class="close-modal" onclick="closeCart()">&times;</span>
            <h2>Your Shopping Cart</h2>
            <div class="cart-items" id="cart-items">
                <!-- Cart items will be added dynamically -->
                <p>Your cart is empty.</p>
            </div>
            <div class="cart-total" id="cart-total">
                Total: $0.00
            </div>
            <button class="checkout-btn">Proceed to Checkout</button>
        </div>
    </div>

    <script>
        // Categories for our products
        const categories = [
            "Electronics",
            "Computers",
            "Smart Home",
            "Arts & Crafts",
            "Automotive",
            "Baby",
            "Beauty",
            "Books",
            "Fashion",
            "Garden",
            "Grocery",
            "Health",
            "Home",
            "Industrial",
            "Luggage",
            "Movies",
            "Music",
            "Pet Supplies",
            "Software",
            "Sports",
            "Tools",
            "Toys",
            "Video Games"
        ];

        // Generate 100 product variants (partial list shown here)
        const products = [
            // Electronics (20 products)
            {
                id: 1,
                title: "Wireless Bluetooth Headphones",
                price: 59.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1505740420928-5e560c06d30e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { color: "Black", price: 59.99 },
                    { color: "White", price: 62.99 },
                    { color: "Blue", price: 59.99 },
                    { color: "Red", price: 64.99 }
                ],
                keywords: ["headphones", "bluetooth", "wireless", "audio"]
            },
            {
                id: 2,
                title: "Noise Cancelling Headphones Pro",
                price: 199.99,
                rating: 5,
                image: "https://images.unsplash.com/photo-1505740420928-5e560c06d30e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { color: "Black", price: 199.99 },
                    { color: "Silver", price: 209.99 },
                    { color: "Gold", price: 219.99 }
                ],
                keywords: ["headphones", "noise cancelling", "premium", "audio"]
            },
            {
                id: 3,
                title: "Smart Watch with Fitness Tracker",
                price: 89.99,
                rating: 5,
                image: "https://images.unsplash.com/photo-1523275335684-37898b6baf30?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1399&q=80",
                category: "Electronics",
                variants: [
                    { size: "Small", color: "Black", price: 89.99 },
                    { size: "Medium", color: "Black", price: 89.99 },
                    { size: "Large", color: "Black", price: 89.99 },
                    { size: "Small", color: "Rose Gold", price: 94.99 },
                    { size: "Medium", color: "Rose Gold", price: 94.99 }
                ],
                keywords: ["smartwatch", "fitness", "tracker", "wearable"]
            },
            {
                id: 4,
                title: "Wireless Charging Stand",
                price: 29.99,
                rating: 3,
                image: "https://images.unsplash.com/photo-1583394838336-acd977736f90?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { color: "White", price: 29.99 },
                    { color: "Black", price: 29.99 }
                ],
                keywords: ["charger", "wireless", "charging", "stand"]
            },
            {
                id: 5,
                title: "Bluetooth Speaker",
                price: 49.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1572569511254-d8f925fe2cbb?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1458&q=80",
                category: "Electronics",
                variants: [
                    { color: "Black", price: 49.99 },
                    { color: "Blue", price: 49.99 },
                    { color: "Red", price: 52.99 }
                ],
                keywords: ["speaker", "bluetooth", "portable", "audio"]
            },
            {
                id: 6,
                title: "4K Action Camera",
                price: 129.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1516035069371-29a1b244cc32?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1528&q=80",
                category: "Electronics",
                variants: [
                    { model: "Basic", price: 129.99 },
                    { model: "Pro", price: 169.99 },
                    { model: "Ultra", price: 199.99 }
                ],
                keywords: ["camera", "action", "4k", "video"]
            },
            {
                id: 7,
                title: "Digital SLR Camera",
                price: 499.99,
                rating: 5,
                image: "https://images.unsplash.com/photo-1510127034890-ba27508e9f1c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { lens: "18-55mm", price: 499.99 },
                    { lens: "18-135mm", price: 699.99 },
                    { lens: "18-200mm", price: 899.99 }
                ],
                keywords: ["camera", "dslr", "photography", "professional"]
            },
            {
                id: 8,
                title: "E-Reader",
                price: 129.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1544947950-fa07a98d237f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1587&q=80",
                category: "Electronics",
                variants: [
                    { storage: "8GB", price: 129.99 },
                    { storage: "32GB", price: 159.99 }
                ],
                keywords: ["ereader", "ebook", "reading", "digital"]
            },
            {
                id: 9,
                title: "Fitness Tracker Band",
                price: 39.99,
                rating: 3,
                image: "https://images.unsplash.com/photo-1576243349700-aa8aad4aeeff?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { color: "Black", price: 39.99 },
                    { color: "Blue", price: 39.99 },
                    { color: "Pink", price: 39.99 },
                    { color: "Green", price: 39.99 }
                ],
                keywords: ["fitness", "tracker", "band", "health"]
            },
            {
                id: 10,
                title: "Gaming Mouse",
                price: 49.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1527814050087-3793815479db?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1528&q=80",
                category: "Electronics",
                variants: [
                    { color: "Black", price: 49.99 },
                    { color: "RGB", price: 59.99 }
                ],
                keywords: ["mouse", "gaming", "computer", "accessory"]
            },
            {
                id: 11,
                title: "Mechanical Keyboard",
                price: 79.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1558043711-3f01f9136f54?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { switch: "Red", price: 79.99 },
                    { switch: "Blue", price: 79.99 },
                    { switch: "Brown", price: 79.99 }
                ],
                keywords: ["keyboard", "mechanical", "gaming", "typing"]
            },
            {
                id: 12,
                title: "Portable Projector",
                price: 149.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1563212034-a5a0d1e0c75a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { resolution: "720p", price: 149.99 },
                    { resolution: "1080p", price: 199.99 }
                ],
                keywords: ["projector", "portable", "home theater", "movie"]
            },
            {
                id: 13,
                title: "Smartphone Gimbal",
                price: 89.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1557804506-669a67965ba0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1374&q=80",
                category: "Electronics",
                variants: [
                    { color: "Black", price: 89.99 },
                    { color: "Gray", price: 89.99 }
                ],
                keywords: ["gimbal", "stabilizer", "video", "smartphone"]
            },
            {
                id: 14,
                title: "VR Headset",
                price: 299.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1593508512255-86ab42a8e620?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1478&q=80",
                category: "Electronics",
                variants: [
                    { model: "Standard", price: 299.99 },
                    { model: "Pro", price: 399.99 }
                ],
                keywords: ["vr", "virtual reality", "gaming", "headset"]
            },
            {
                id: 15,
                title: "Wireless Earbuds",
                price: 79.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1590658268037-6bf12165a8df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1632&q=80",
                category: "Electronics",
                variants: [
                    { color: "White", price: 79.99 },
                    { color: "Black", price: 79.99 },
                    { color: "Blue", price: 79.99 }
                ],
                keywords: ["earbuds", "wireless", "bluetooth", "audio"]
            },
            {
                id: 16,
                title: "Digital Photo Frame",
                price: 99.99,
                rating: 3,
                image: "https://images.unsplash.com/photo-1584308666744-24d5c474f2ae?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1630&q=80",
                category: "Electronics",
                variants: [
                    { size: "8-inch", price: 99.99 },
                    { size: "10-inch", price: 129.99 }
                ],
                keywords: ["photo frame", "digital", "picture", "display"]
            },
            {
                id: 17,
                title: "Smart Doorbell",
                price: 149.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1558002038-1055907df827?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { model: "Standard", price: 149.99 },
                    { model: "Pro", price: 199.99 }
                ],
                keywords: ["doorbell", "smart home", "security", "camera"]
            },
            {
                id: 18,
                title: "Robot Vacuum",
                price: 249.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1575300905107-9aa498abf8e0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { model: "Basic", price: 249.99 },
                    { model: "Smart", price: 349.99 },
                    { model: "Ultra", price: 499.99 }
                ],
                keywords: ["vacuum", "robot", "cleaner", "smart home"]
            },
            {
                id: 19,
                title: "Dash Cam",
                price: 89.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1601584115197-04ecc0da31e8?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { resolution: "1080p", price: 89.99 },
                    { resolution: "4K", price: 129.99 }
                ],
                keywords: ["dash cam", "car", "camera", "recorder"]
            },
            {
                id: 20,
                title: "Drone with Camera",
                price: 299.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1579829366248-204fe8413f31?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Electronics",
                variants: [
                    { model: "Beginner", price: 299.99 },
                    { model: "Advanced", price: 499.99 },
                    { model: "Professional", price: 799.99 }
                ],
                keywords: ["drone", "camera", "quadcopter", "aerial"]
            },

            // Computers (15 products)
            {
                id: 21,
                title: "Ultra HD 4K Monitor",
                price: 299.99,
                rating: 5,
                image: "https://images.unsplash.com/photo-1546538915-a9e2c8a0b9a5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { size: "27-inch", price: 299.99 },
                    { size: "32-inch", price: 399.99 }
                ],
                keywords: ["monitor", "4k", "ultra hd", "display"]
            },
            {
                id: 22,
                title: "Gaming Laptop",
                price: 1299.99,
                rating: 5,
                image: "https://images.unsplash.com/photo-1593642632823-8f785ba67e45?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1632&q=80",
                category: "Computers",
                variants: [
                    { ram: "16GB", storage: "512GB", price: 1299.99 },
                    { ram: "32GB", storage: "1TB", price: 1699.99 }
                ],
                keywords: ["laptop", "gaming", "computer", "notebook"]
            },
            {
                id: 23,
                title: "All-in-One Desktop",
                price: 899.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1586211089455-813f6b9a1f0f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { ram: "8GB", storage: "256GB", price: 899.99 },
                    { ram: "16GB", storage: "512GB", price: 1099.99 }
                ],
                keywords: ["desktop", "all-in-one", "computer", "workstation"]
            },
            {
                id: 24,
                title: "External SSD Drive",
                price: 89.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1591488320449-011701bb6704?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { capacity: "500GB", price: 89.99 },
                    { capacity: "1TB", price: 149.99 },
                    { capacity: "2TB", price: 249.99 }
                ],
                keywords: ["ssd", "external", "storage", "hard drive"]
            },
            {
                id: 25,
                title: "Wireless Keyboard & Mouse Combo",
                price: 49.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1615663245857-ac93bb7c39e7?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { color: "Black", price: 49.99 },
                    { color: "White", price: 49.99 }
                ],
                keywords: ["keyboard", "mouse", "wireless", "combo"]
            },
            {
                id: 26,
                title: "USB-C Hub with 4 Ports",
                price: 29.99,
                rating: 3,
                image: "https://images.unsplash.com/photo-1592899677977-9c10ca588bbd?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1528&q=80",
                category: "Computers",
                variants: [
                    { ports: "4-in-1", price: 29.99 },
                    { ports: "6-in-1", price: 39.99 },
                    { ports: "8-in-1", price: 49.99 }
                ],
                keywords: ["usb-c", "hub", "adapter", "ports"]
            },
            {
                id: 27,
                title: "Ergonomic Office Chair",
                price: 199.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1598300042247-d088f8ab3a91?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1632&q=80",
                category: "Computers",
                variants: [
                    { color: "Black", price: 199.99 },
                    { color: "Gray", price: 199.99 }
                ],
                keywords: ["chair", "ergonomic", "office", "desk"]
            },
            {
                id: 28,
                title: "Standing Desk Converter",
                price: 149.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1518455027359-f3f8164ba6bd?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1633&q=80",
                category: "Computers",
                variants: [
                    { size: "Large", price: 149.99 },
                    { size: "X-Large", price: 179.99 }
                ],
                keywords: ["desk", "standing", "converter", "ergonomic"]
            },
            {
                id: 29,
                title: "Webcam with Microphone",
                price: 59.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1585771724684-38269d6639fd?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { resolution: "1080p", price: 59.99 },
                    { resolution: "4K", price: 99.99 }
                ],
                keywords: ["webcam", "camera", "microphone", "video"]
            },
            {
                id: 30,
                title: "Noise Cancelling Headset",
                price: 129.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1505740420928-5e560c06d30e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { color: "Black", price: 129.99 },
                    { color: "White", price: 129.99 }
                ],
                keywords: ["headset", "noise cancelling", "microphone", "audio"]
            },
            {
                id: 31,
                title: "Laptop Cooling Pad",
                price: 29.99,
                rating: 3,
                image: "https://images.unsplash.com/photo-1592155931584-901ac15763e3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1473&q=80",
                category: "Computers",
                variants: [
                    { size: "15-inch", price: 29.99 },
                    { size: "17-inch", price: 34.99 }
                ],
                keywords: ["cooling pad", "laptop", "accessory", "stand"]
            },
            {
                id: 32,
                title: "Monitor Arm Mount",
                price: 79.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1595341595379-cf1cd0fb7fb3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { arms: "Single", price: 79.99 },
                    { arms: "Dual", price: 119.99 }
                ],
                keywords: ["monitor", "arm", "mount", "stand"]
            },
            {
                id: 33,
                title: "Laptop Backpack",
                price: 49.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1553062407-98eeb64c6a62?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1587&q=80",
                category: "Computers",
                variants: [
                    { color: "Black", price: 49.99 },
                    { color: "Gray", price: 49.99 },
                    { color: "Blue", price: 49.99 }
                ],
                keywords: ["backpack", "laptop", "bag", "carry"]
            },
            {
                id: 34,
                title: "Wireless Presenter",
                price: 29.99,
                rating: 3,
                image: "https://images.unsplash.com/photo-1581092918056-0c4c3acd3789?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { range: "50ft", price: 29.99 },
                    { range: "100ft", price: 39.99 }
                ],
                keywords: ["presenter", "wireless", "pointer", "remote"]
            },
            {
                id: 35,
                title: "Document Scanner",
                price: 149.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1581093057305-25a0a6b9c8b3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Computers",
                variants: [
                    { speed: "20ppm", price: 149.99 },
                    { speed: "30ppm", price: 199.99 }
                ],
                keywords: ["scanner", "document", "office", "scan"]
            },

            // Smart Home (15 products)
            {
                id: 36,
                title: "Smart Thermostat",
                price: 199.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1556740738-b6a63e27c4df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { model: "Basic", price: 199.99 },
                    { model: "Learning", price: 249.99 }
                ],
                keywords: ["thermostat", "smart", "home", "temperature"]
            },
            {
                id: 37,
                title: "Smart Light Bulbs (4-Pack)",
                price: 49.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1517486808906-6ca8b3f8e1c1?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1587&q=80",
                category: "Smart Home",
                variants: [
                    { color: "White", price: 49.99 },
                    { color: "RGB", price: 59.99 }
                ],
                keywords: ["light bulbs", "smart", "led", "lights"]
            },
            {
                id: 38,
                title: "Video Doorbell",
                price: 179.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1558002038-1055907df827?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { resolution: "1080p", price: 179.99 },
                    { resolution: "2K", price: 229.99 }
                ],
                keywords: ["doorbell", "video", "security", "smart"]
            },
            {
                id: 39,
                title: "Smart Plug",
                price: 24.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1585771724684-38269d6639fd?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { pack: "Single", price: 24.99 },
                    { pack: "2-Pack", price: 39.99 },
                    { pack: "4-Pack", price: 69.99 }
                ],
                keywords: ["smart plug", "outlet", "remote", "control"]
            },
            {
                id: 40,
                title: "Smart Lock",
                price: 199.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1566228015668-4c45dbc4e2f5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1587&q=80",
                category: "Smart Home",
                variants: [
                    { type: "Keypad", price: 199.99 },
                    { type: "Fingerprint", price: 249.99 }
                ],
                keywords: ["lock", "smart", "door", "security"]
            },
            {
                id: 41,
                title: "Security Camera",
                price: 129.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1563986768609-322da13575f3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { resolution: "1080p", price: 129.99 },
                    { resolution: "2K", price: 159.99 },
                    { resolution: "4K", price: 199.99 }
                ],
                keywords: ["camera", "security", "monitor", "surveillance"]
            },
            {
                id: 42,
                title: "Robot Vacuum",
                price: 249.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1575300905107-9aa498abf8e0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { model: "Basic", price: 249.99 },
                    { model: "Smart", price: 349.99 }
                ],
                keywords: ["vacuum", "robot", "cleaner", "smart"]
            },
            {
                id: 43,
                title: "Smart Blinds",
                price: 149.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1558036117-15e82a5b9dc6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { size: "Small", price: 149.99 },
                    { size: "Medium", price: 179.99 },
                    { size: "Large", price: 199.99 }
                ],
                keywords: ["blinds", "smart", "window", "shades"]
            },
            {
                id: 44,
                title: "Air Quality Monitor",
                price: 129.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1585771724684-38269d6639fd?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { features: "Basic", price: 129.99 },
                    { features: "Advanced", price: 179.99 }
                ],
                keywords: ["air quality", "monitor", "sensor", "health"]
            },
            {
                id: 45,
                title: "Smart Scale",
                price: 49.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { capacity: "400lb", price: 49.99 },
                    { capacity: "500lb", price: 59.99 }
                ],
                keywords: ["scale", "smart", "weight", "health"]
            },
            {
                id: 46,
                title: "Smart Sprinkler Controller",
                price: 129.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1581093057305-25a0a6b9c8b3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { zones: "8", price: 129.99 },
                    { zones: "16", price: 179.99 }
                ],
                keywords: ["sprinkler", "controller", "smart", "garden"]
            },
            {
                id: 47,
                title: "Smart Smoke Detector",
                price: 119.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1585771724684-38269d6639fd?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { type: "Smoke", price: 119.99 },
                    { type: "Smoke + CO", price: 149.99 }
                ],
                keywords: ["smoke", "detector", "alarm", "safety"]
            },
            {
                id: 48,
                title: "Smart Garage Door Opener",
                price: 199.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1563986768609-322da13575f3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { model: "Basic", price: 199.99 },
                    { model: "Pro", price: 249.99 }
                ],
                keywords: ["garage", "door", "opener", "smart"]
            },
            {
                id: 49,
                title: "Water Leak Detector",
                price: 49.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1581093057305-25a0a6b9c8b3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { pack: "Single", price: 49.99 },
                    { pack: "3-Pack", price: 119.99 }
                ],
                keywords: ["water", "leak", "detector", "sensor"]
            },
            {
                id: 50,
                title: "Smart Ceiling Fan",
                price: 199.99,
                rating: 4,
                image: "https://images.unsplash.com/photo-1558036117-15e82a5b9dc6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
                category: "Smart Home",
                variants: [
                    { size: "52-inch", price: 199.99 },
                    { size: "60-inch", price: 249.99 }
                ],
                keywords: ["fan", "ceiling", "smart", "cooling"]
            }

            // Remaining products can be appended here...
        ];

        // Shopping cart
        let cart = [];

        // DOM elements
        const featuredGrid = document.getElementById('featured-grid');
        const categoryTabs = document.getElementById('category-tabs');
        const cartModal = document.getElementById('cart-modal');
        const cartItems = document.getElementById('cart-items');
        const cartCount = document.getElementById('cart-count');
        const cartTotal = document.getElementById('cart-total');
        const searchInput = document.getElementById('search-input');
        const searchButton = document.getElementById('search-button');
        const mainContent = document.getElementById('main-content');

        // Initialize the page
        function init() {
            renderCategories();
            renderFeaturedProducts();
            setupEventListeners();
        }

        // Render category tabs
        function renderCategories() {
            categories.forEach(category => {
                const tab = document.createElement('div');
                tab.className = 'category-tab';
                tab.textContent = category;
                tab.addEventListener('click', () => filterByCategory(category));
                categoryTabs.appendChild(tab);
            });

            // Set first tab as active
            if (categoryTabs.firstChild) {
                categoryTabs.firstChild.classList.add('active');
            }
        }

        // Render featured products
        function renderFeaturedProducts() {
            featuredGrid.innerHTML = '';
            products.slice(0, 12).forEach(product => {
                featuredGrid.appendChild(createProductCard(product));
            });
        }

        // Create product card element
        function createProductCard(product) {
            const card = document.createElement('div');
            card.className = 'product-card';
            card.dataset.id = product.id;
            card.dataset.category = product.category;
            card.dataset.keywords = (product.keywords || []).join(',');

            // Generate variant text
            let variantText = '';
            if (product.variants && product.variants.length > 0) {
                const firstVariant = product.variants[0];
                const variantKeys = Object.keys(firstVariant).filter(key => key !== 'price');
                variantText = variantKeys.map(key => `${key}: ${firstVariant[key] || ''}`).join(', ');
                
                if (product.variants.length > 1) {
                    variantText += ` + ${product.variants.length - 1} more`;
                }
            }

            card.innerHTML = `
                <div class="product-image">
                    <img src="${product.image}" alt="${product.title}">
                </div>
                <div class="product-title">${product.title}</div>
                <div class="product-price">$${Number(product.price).toFixed(2)}</div>
                <div class="product-rating">${'★'.repeat(product.rating || 0)}${'☆'.repeat(5 - (product.rating || 0))}</div>
                ${variantText ? `<div class="product-variants">${variantText}</div>` : ''}
                <button class="add-to-cart">Add to Cart</button>
            `;

            // Add click event to add to cart button
            const addBtn = card.querySelector('.add-to-cart');
            if (addBtn) addBtn.addEventListener('click', () => addToCart(product));

            return card;
        }

        // Filter products by category
        function filterByCategory(category) {
            // Update active tab
            document.querySelectorAll('.category-tab').forEach(tab => {
                tab.classList.remove('active');
                if (tab.textContent === category) {
                    tab.classList.add('active');
                }
            });

            // Filter and display products
            featuredGrid.innerHTML = '';
            const filteredProducts = products.filter(p => p.category === category);
            if (filteredProducts.length) {
                filteredProducts.forEach(product => {
                    featuredGrid.appendChild(createProductCard(product));
                });
            } else {
                featuredGrid.innerHTML = '<div class="no-results">No products in this category.</div>';
            }
        }

        // Search products
        function searchProducts(query) {
            if (!query || !query.trim()) {
                renderFeaturedProducts();
                return;
            }

            const q = query.toLowerCase();
            const results = products.filter(product => 
                (product.title && product.title.toLowerCase().includes(q)) ||
                (product.keywords && product.keywords.some(kw => kw.toLowerCase().includes(q)))
            );

            featuredGrid.innerHTML = '';
            if (results.length > 0) {
                results.forEach(product => {
                    featuredGrid.appendChild(createProductCard(product));
                });
            } else {
                featuredGrid.innerHTML = '<div class="no-results">No products found matching your search.</div>';
            }
        }

        // Add product to cart
        function addToCart(product) {
            // Check if product already in cart
            const existingItem = cart.find(item => item.id === product.id);
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({
                    ...product,
                    quantity: 1,
                    selectedVariant: product.variants ? product.variants[0] : null
                });
            }

            updateCart();
            showCartNotification();
        }

        // Update cart UI
        function updateCart() {
            // Update cart count
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            cartCount.textContent = totalItems;

            // Update cart modal if open
            if (cartModal.style.display === 'block') {
                renderCartItems();
            }
        }

        // Show cart notification
        function showCartNotification() {
            const notification = document.createElement('div');
            notification.className = 'cart-notification';
            notification.textContent = 'Item added to cart';
            notification.style.position = 'fixed';
            notification.style.bottom = '20px';
            notification.style.right = '20px';
            notification.style.backgroundColor = '#FFD814';
            notification.style.padding = '10px 20px';
            notification.style.borderRadius = '4px';
            notification.style.boxShadow = '0 2px 5px rgba(0,0,0,0.2)';
            notification.style.zIndex = '1000';
            document.body.appendChild(notification);

            setTimeout(() => {
                notification.style.opacity = '0';
                notification.style.transition = 'opacity 0.5s';
                setTimeout(() => notification.remove(), 500);
            }, 2000);
        }

        // Render cart items in modal
        function renderCartItems() {
            if (cart.length === 0) {
                cartItems.innerHTML = '<p>Your cart is empty.</p>';
                cartTotal.textContent = 'Total: $0.00';
                return;
            }

            cartItems.innerHTML = '';
            let total = 0;

            cart.forEach(item => {
                const cartItem = document.createElement('div');
                cartItem.className = 'cart-item';
                cartItem.dataset.id = item.id;

                const subtotal = item.price * item.quantity;
                total += subtotal;

                cartItem.innerHTML = `
                    <div class="cart-item-image">
                        <img src="${item.image}" alt="${item.title}">
                    </div>
                    <div class="cart-item-details">
                        <div class="cart-item-title">${item.title}</div>
                        <div class="cart-item-price">$${Number(item.price).toFixed(2)}</div>
                        <div class="cart-item-quantity">
                            <button class="quantity-btn minus">-</button>
                            <input type="text" class="quantity-input" value="${item.quantity}">
                            <button class="quantity-btn plus">+</button>
                        </div>
                        <div class="remove-item">Delete</div>
                    </div>
                `;

                // Add event listeners
                cartItem.querySelector('.minus').addEventListener('click', () => updateQuantity(item, -1));
                cartItem.querySelector('.plus').addEventListener('click', () => updateQuantity(item, 1));
                cartItem.querySelector('.remove-item').addEventListener('click', () => removeItem(item));

                cartItems.appendChild(cartItem);
            });

            cartTotal.textContent = `Total: $${total.toFixed(2)}`;
        }

        // Update item quantity
        function updateQuantity(item, change) {
            item.quantity += change;
            if (item.quantity < 1) {
                item.quantity = 1;
            }
            updateCart();
        }

        // Remove item from cart
        function removeItem(item) {
            cart = cart.filter(cartItem => cartItem.id !== item.id);
            updateCart();
        }

        // Open cart modal
        function openCart() {
            cartModal.style.display = 'block';
            renderCartItems();
        }

        // Close cart modal
        function closeCart() {
            cartModal.style.display = 'none';
        }

        // Setup event listeners
        function setupEventListeners() {
            // Close modal when clicking outside
            window.addEventListener('click', (e) => {
                if (e.target === cartModal) {
                    closeCart();
                }
            });

            // Search functionality
            searchButton.addEventListener('click', () => {
                searchProducts(searchInput.value);
            });

            searchInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    searchProducts(searchInput.value);
                }
            });
        }

        // Initialize the app
        init();
    </script>
</body>
</html>
