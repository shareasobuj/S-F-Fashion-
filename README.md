# S-F-Fashion

<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>s&f fashion.com - Garments Buying House</title>
<style>
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0; padding: 0; background: #f5f7fa;
  }
  header {
    background: #0077cc; color: white;
    padding: 1rem 2rem;
    text-align: center;
  }
  header h1 {
    margin: 0;
  }
  main {
    max-width: 900px; margin: 2rem auto;
    background: white; padding: 2rem;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    border-radius: 6px;
  }
  h2 {
    margin-top: 0;
  }
  form > * {
    display: block;
    width: 100%;
    margin: 0.5rem 0 1rem 0;
    padding: 0.5rem;
    font-size: 1rem;
  }
  label {
    font-weight: 600;
    margin-top: 1rem;
  }
  button {
    background: #0077cc;
    border: none;
    color: white;
    padding: 0.7rem 1rem;
    font-size: 1rem;
    cursor: pointer;
    border-radius: 4px;
  }
  button:hover {
    background: #005fa3;
  }
  .products {
    margin-top: 2rem;
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(250px,1fr));
    gap: 1rem;
  }
  .product-card {
    background: #eef4fb;
    padding: 1rem;
    border-radius: 6px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.1);
    position: relative;
  }
  .product-card img {
    max-width: 100%;
    height: 140px;
    object-fit: contain;
    margin-bottom: 1rem;
    background: white;
    border-radius: 4px;
  }
  .product-card h3 {
    margin: 0.3rem 0;
  }
  .product-card p {
    margin: 0.2rem 0;
    font-weight: bold;
  }
  .product-card button {
    position: absolute;
    top: 10px; right: 10px;
    background: #cc3300;
    font-size: 0.85rem;
    padding: 0.3rem 0.6rem;
  }
  .order-section {
    margin-top: 3rem;
    padding-top: 1rem;
    border-top: 1px solid #ccc;
  }
  .order-section textarea {
    height: 80px;
    resize: vertical;
  }
  .orders-list {
    margin-top: 1rem;
    max-height: 150px;
    overflow-y: auto;
    background: #f0f4ff;
    padding: 1rem;
    border-radius: 6px;
  }
  .orders-list div {
    margin-bottom: 0.5rem;
    padding-bottom: 0.5rem;
    border-bottom: 1px dotted #0077cc;
  }
  .contact-info {
    margin-top: 3rem;
    padding-top: 1rem;
    border-top: 1px solid #ddd;
    font-size: 0.95rem;
    color: #444;
  }
  .contact-info strong {
    display: inline-block;
    width: 150px;
  }
  .footer {
    text-align: center;
    margin: 3rem 0 1rem 0;
    color: #777;
    font-size: 0.9rem;
  }
  a.contact-link {
    color: #0077cc;
    text-decoration: none;
  }
  a.contact-link:hover {
    text-decoration: underline;
  }
</style>
</head>
<body>
<header>
  <h1>s&f fashion.com</h1>
  <p>Garments Buying House - Manage your products and orders dynamically</p>
</header>
<main>
  <section class="product-management">
    <h2>Manage Products</h2>
    <form id="product-form">
      <label for="name">Product Name:</label>
      <input type="text" id="name" required placeholder="Example: Cotton T-Shirt" />
      
      <label for="price">Price (USD):</label>
      <input type="number" id="price" required min="0" step="0.01" placeholder="e.g. 12.50" />
      
      <label for="image-url">Image URL:</label>
      <input type="url" id="image-url" required placeholder="http://example.com/image.jpg" />
      
      <button type="submit">Add Product</button>
    </form>

    <div class="products" id="products-list">
      <!-- Products will appear here -->
    </div>
  </section>

  <section class="order-section">
    <h2>Place an Order</h2>
    <form id="order-form">
      <label for="order-details">Order Details:</label>
      <textarea id="order-details" required placeholder="Write your order details here..."></textarea>
      <button type="submit">Submit Order</button>
    </form>

    <h3>Orders</h3>
    <div class="orders-list" id="orders-list">
      <!-- Orders will appear here -->
    </div>
  </section>

  <section class="contact-info">
    <h2>Contact Information</h2>
    <p><strong>Managing Director:</strong> SHAREA SOBUJ SHISHIR</p>
    <p><strong>Email:</strong> <a class="contact-link" href="mailto:shareasobuj9829@gmail.com">shareasobuj9829@gmail.com</a></p>
    <p><strong>Phone:</strong> <a class="contact-link" href="tel:+8801310289829">01310289829</a></p>
  </section>
</main>
<div class="footer">
  &copy; 2025 s&f fashion.com
</div>

<script>
  // ডিফল্ট প্রোডাক্ট লিস্ট, যেগুলো ছবিসহ সাইট লোড হলে দেখাবে
  let defaultProducts = [
    {
      name: "Cotton Casual Shirt",
      price: "15.99",
      image: "https://images.unsplash.com/photo-1521334884684-d80222895322?auto=format&fit=crop&w=400&q=80"
    },
    {
      name: "Denim Jeans",
      price: "25.50",
      image: "https://images.unsplash.com/photo-1512436991641-6745cdb1723f?auto=format&fit=crop&w=400&q=80"
    },
    {
      name: "Formal Blazer",
      price: "45.00",
      image: "https://images.unsplash.com/photo-1514996937319-344454492b37?auto=format&fit=crop&w=400&q=80"
    }
  ];

  // লোকালস্টোরেজ থেকে ডেটা লোড, না থাকলে ডিফল্ট প্রোডাক্ট ব্যবহার
  let products = JSON.parse(localStorage.getItem('products'));
  if (!products || products.length === 0) {
    products = defaultProducts;
    localStorage.setItem('products', JSON.stringify(products));
  }

  let orders = JSON.parse(localStorage.getItem('orders')) || [];

  const productsListEl = document.getElementById('products-list');
  const ordersListEl = document.getElementById('orders-list');
  const productForm = document.getElementById('product-form');
  const orderForm = document.getElementById('order-form');

  function renderProducts() {
    productsListEl.innerHTML = '';
    if(products.length === 0){
      productsListEl.innerHTML = '<p>No products added yet.</p>';
      return;
    }
    products.forEach((prod, index) => {
      const card = document.createElement('div');
      card.className = 'product-card';

      card.innerHTML = `
        <img src="${prod.image}" alt="${prod.name}" />
        <h3>${prod.name}</h3>
        <p>Price: $${parseFloat(prod.price).toFixed(2)}</p>
        <button onclick="deleteProduct(${index})">Delete</button>
      `;

      productsListEl.appendChild(card);
    });
  }

  function deleteProduct(index){
    if(confirm('Are you sure you want to delete this product?')){
      products.splice(index, 1);
      saveProducts();
      renderProducts();
    }
  }

  function saveProducts(){
    localStorage.setItem('products', JSON.stringify(products));
  }

  productForm.addEventListener('submit', (e) => {
    e.preventDefault();
    const name = document.getElementById('name').value.trim();
    const price = document.getElementById('price').value.trim();
    const image = document.getElementById('image-url').value.trim();

    if(name && price && image){
      products.push({name, price, image});
      saveProducts();
      renderProducts();
      productForm.reset();
      alert('Product added successfully!');
    } else {
      alert('Please fill all fields properly.');
    }
  });

  function renderOrders(){
    ordersListEl.innerHTML = '';
    if(orders.length === 0){
      ordersListEl.innerHTML = '<p>No orders placed yet.</p>';
      return;
    }
    orders.forEach((order, i) => {
      const div = document.createElement('div');
      div.textContent = `Order #${i + 1}: ${order.details}`;
      ordersListEl.appendChild(div);
    });
  }

  function saveOrders(){
    localStorage.setItem('orders', JSON.stringify(orders));
  }

  orderForm.addEventListener('submit', (e) => {
    e.preventDefault();
    const details = document.getElementById('order-details').value.trim();
    if(details){
      orders.push({details});
      saveOrders();
      renderOrders();
      orderForm.reset();
      alert('Order placed successfully!');
    } else {
      alert('Please enter order details.');
    }
  });

  renderProducts();
  renderOrders();
</script>

</body>
</html>
