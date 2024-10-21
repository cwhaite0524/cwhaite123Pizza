# cwhaite123Pizza.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crust & Co</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #f7f7f7;
            color: #4f0d0d;
        }
        header {
            background-color: #4f0d0d;
            color: white;
            padding: 1rem;
            text-align: center;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        h1 {
            margin: 0;
            font-size: 2.5em;
            font-weight: 600;
        }
        nav {
            background-color: #F39666;
            padding: 0.5rem;
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        nav ul {
            list-style-type: none;
            padding: 0;
            margin: 0;
            display: flex;
            justify-content: center;
        }
        nav ul li {
            margin: 0 15px;
        }
        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 600;
            padding: 5px 10px;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        nav ul li a:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }
        .container {
            width: 90%;
            max-width: 1200px;
            margin: auto;
            padding: 20px;
        }
        .menu-item {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }
        .menu-item:hover {
            transform: translateY(-5px);
        }
        .menu-item h4 {
            color: #ff6b6b;
            margin-top: 0;
        }
        button {
            background-color: #4ecdc4;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #45b7aa;
        }
        .page {
            display: none;
            animation: fadeIn 0.5s;
        }
        .page.active {
            display: block;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        #cart-icon {
            position: fixed;
            top: 20px;
            right: 20px;
            background-color: #ff6b6b;
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 1001;
        }
        #cart-count {
            position: absolute;
            top: -5px;
            right: -5px;
            background-color: #4ecdc4;
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 12px;
        }
        #checkout {
            position: fixed;
            top: 0;
            right: -300px;
            width: 300px;
            height: 100%;
            background-color: white;
            box-shadow: -2px 0 5px rgba(0, 0, 0, 0.1);
            transition: right 0.3s;
            z-index: 1002;
            padding: 20px;
            box-sizing: border-box;
            overflow-y: auto;
        }
        #checkout.active {
            right: 0;
        }
        #close-checkout {
            position: absolute;
            top: 10px;
            right: 10px;
            cursor: pointer;
            font-size: 20px;
        }
        form {
            margin-top: 20px;
        }
        input, select {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        input[type="submit"] {
            background-color: #4ecdc4;
            color: white;
            border: none;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        input[type="submit"]:hover {
            background-color: #45b7aa;
        }
        /* Adding height to the image */
        img {
            height: 200px; /* Change to your desired height */
            width: auto; /* Maintain aspect ratio */
            display: block; /* Centering image when it's a block */
            margin: 20px auto; /* Centering the image with margin */
        }
    </style>
</head>
<body>
    <header>
        <h1>Crust & Co</h1>
    </header>
    <nav>
        <ul>
            <li><a onclick="showPage('home')">Home</a></li>
            <li><a onclick="showPage('menu')">Menu</a></li>
            <li><a onclick="showPage('info')">Store Info</a></li>
        </ul>
    </nav>

    <div id="cart-icon" onclick="toggleCheckout()">
        🛒
        <span id="cart-count">0</span>
    </div>

    <div id="checkout">
        <span id="close-checkout" onclick="toggleCheckout()">✖</span>
        <h2>Your Cart</h2>
        <ul id="cart-items"></ul>
        <p>Total: $<span id="cart-total">0</span></p>
        <form id="order-form">
            <h3>Order Details</h3>
            <input type="text" id="name" placeholder="Your Name" required>
            <input type="email" id="email" placeholder="Your Email" required>
            <input type="text" id="phone" placeholder="Your Phone Number" required>
            <input type="text" id="address" placeholder="Delivery Address">
            <select id="order-type" required>
                <option value="">Select Order Type</option>
                <option value="delivery">Delivery</option>
                <option value="pickup">Pickup</option>
            </select>
            <input type="submit" value="Place Order">
        </form>
    </div>

    <div class="container">
        <div id="home" class="page active">
            <h2>Welcome to Crust & Co</h2>
            <p>Indulge in our delicious pizzas, available for pickup and delivery. Each pie is crafted with the freshest ingredients and topped with a blend of mouthwatering cheeses, ensuring a symphony of flavors in every bite. Whether you prefer classic favorites like Margherita and Pepperoni, or you're feeling adventurous with our gourmet options like Truffle Mushroom and BBQ Chicken, there's something to tantalize every palate.</p>
        </div>

        <img src="gallery1.jpg"> 

        <div id="menu" class="page">
            <h2>Our Menu</h2>
            <div id="pizza-menu">
                <h3>Pizzas</h3>
                <div class="menu-item">
                    <h4>Margherita</h4>
                    <p>Classic tomato sauce, mozzarella, and basil</p>
                    <button onclick="addToCart('Margherita', 12)">Add to Cart - $12</button>
                </div>
                <div class="menu-item">
                    <h4>Pepperoni</h4>
                    <p>Tomato sauce, mozzarella, and pepperoni</p>
                    <button onclick="addToCart('Pepperoni', 14)">Add to Cart - $14</button>
                </div>
                <div class="menu-item">
                    <h4>Vegetarian</h4>
                    <p>Tomato sauce, mozzarella, bell peppers, onions, and mushrooms</p>
                    <button onclick="addToCart('Vegetarian', 13)">Add to Cart - $13</button>
                </div>
                <div class="menu-item">
                    <h4>Hawaiian</h4>
                    <p>Tomato sauce, mozzarella, ham, and pineapple</p>
                    <button onclick="addToCart('Hawaiian', 15)">Add to Cart - $15</button>
                </div>
                <div class="menu-item">
                    <h4>BBQ Chicken</h4>
                    <p>BBQ sauce, mozzarella, grilled chicken, and red onions</p>
                    <button onclick="addToCart('BBQ Chicken', 16)">Add to Cart - $16</button>
                </div>
                <div class="menu-item">
                    <h4>Supreme</h4>
                    <p>Tomato sauce, mozzarella, pepperoni, sausage, bell peppers, onions, and olives</p>
                    <button onclick="addToCart('Supreme', 17)">Add to Cart - $17</button>
                </div>
            </div>
            
            <div id="drinks-menu">
                <h3>Soft Drinks</h3>
                <div class="menu-item">
                    <h4>Cola</h4>
                    <button onclick="addToCart('Cola', 2)">Add to Cart - $2</button>
                </div>
                <div class="menu-item">
                    <h4>Lemon-Lime Soda</h4>
                    <button onclick="addToCart('Lemon-Lime Soda', 2)">Add to Cart - $2</button>
                </div>
                <div class="menu-item">
                    <h4>Orange Soda</h4>
                    <button onclick="addToCart('Orange Soda', 2)">Add to Cart - $2</button>
                </div>
            </div>
            
            <div id="special-menu">
                <h3>Special</h3>
                <div class="menu-item">
                    <h4>Family Meal Deal</h4>
                    <p>2 large pizzas, 4 soft drinks, and a dozen donuts</p>
                    <button onclick="addToCart('Family Meal Deal', 30)">Add to Cart - $30</button>
                </div>
            </div>
        </div>

        <div id="info" class="page">
            <h2>Store Information</h2>
            <p>Address: 123 Pizza Street, Pizzaville, PZ 12345</p>
            <p>Phone: (555) 123-4567</p>
            <p>Hours: Mon-Sun 11:00 AM - 10:00 PM</p>
        </div>
    </div>

    <script>
        let cart = [];
        
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            document.getElementById(pageId).classList.add('active');
        }
        
        function addToCart(item, price) {
            cart.push({item, price});
            updateCart();
            showCheckout();
        }
        
        function updateCart() {
            const cartItems = document.getElementById('cart-items');
            const cartTotal = document.getElementById('cart-total');
            const cartCount = document.getElementById('cart-count');
            
            cartItems.innerHTML = '';
            let total = 0;
            
            cart.forEach(item => {
                const li = document.createElement('li');
                li.textContent = `${item.item} - $${item.price}`;
                cartItems.appendChild(li);
                total += item.price;
            });
            
            cartTotal.textContent = total;
            cartCount.textContent = cart.length;
        }
        
        function toggleCheckout() {
            document.getElementById('checkout').classList.toggle('active');
        }
        
        function showCheckout() {
            document.getElementById('checkout').classList.add('active');
        }
        a
        document.getElementById('order-form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Order placed successfully!');
            cart = [];
            updateCart();
            toggleCheckout();
        });
    </script>
</body>
</html>
