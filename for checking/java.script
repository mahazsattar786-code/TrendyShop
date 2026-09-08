const products = [
  { id: 1, name: "Wireless Earbuds", price: 29.99, image: "https://via.placeholder.com/250?text=Earbuds" },
  { id: 2, name: "Smart Fitness Watch", price: 49.99, image: "https://via.placeholder.com/250?text=Smartwatch" },
  { id: 3, name: "Portable Ring Light", price: 19.99, image: "https://via.placeholder.com/250?text=Ring+Light" },
  { id: 4, name: "Ergonomic Desk Mat", price: 15.99, image: "https://via.placeholder.com/250?text=Desk+Mat" }
];

let cart = [];

const productGrid = document.getElementById("product-grid");
const cartDrawer = document.getElementById("cart-drawer");
const cartBtn = document.getElementById("cart-btn");
const closeCart = document.getElementById("close-cart");
const cartItemsContainer = document.getElementById("cart-items");
const cartCount = document.getElementById("cart-count");
const cartTotal = document.getElementById("cart-total");

// Display Products
function renderProducts() {
  productGrid.innerHTML = products.map(product => `
    <div class="product-card">
      <img src="${product.image}" alt="${product.name}">
      <h3>${product.name}</h3>
      <p class="price">$${product.price.toFixed(2)}</p>
      <button class="add-btn" onclick="addToCart(${product.id})">Add to Cart</button>
    </div>
  `).join('');
}

// Add Item to Cart
function addToCart(productId) {
  const product = products.find(p => p.id === productId);
  cart.push(product);
  updateCart();
  cartDrawer.classList.add("open");
}

// Update Cart View
function updateCart() {
  cartCount.innerText = cart.length;
  
  cartItemsContainer.innerHTML = cart.map((item, index) => `
    <div class="cart-item">
      <div>
        <strong>${item.name}</strong>
        <p>$${item.price.toFixed(2)}</p>
      </div>
      <button onclick="removeFromCart(${index})" style="color:red; border:none; background:none; cursor:pointer;">Remove</button>
    </div>
  `).join('');

  const total = cart.reduce((sum, item) => sum + item.price, 0);
  cartTotal.innerText = total.toFixed(2);
}

// Remove Item from Cart
function removeFromCart(index) {
  cart.splice(index, 1);
  updateCart();
}

// Drawer Toggle
cartBtn.addEventListener("click", () => cartDrawer.classList.add("open"));
closeCart.addEventListener("click", () => cartDrawer.classList.remove("open"));

renderProducts();