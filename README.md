<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Men's Collection - Promota</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      background: url('https://images.unsplash.com/photo-1519744792095-2f2205e87b6f') center/cover no-repeat fixed;
      color: #333;
    }
    header {
      background-color: #000;
      color: white;
      padding: 1rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    nav a {
      color: white;
      margin-left: 1.5rem;
      text-decoration: none;
      font-weight: 500;
    }
    nav a:hover {
      color: #ff6600;
    }
    .hero {
      background: rgba(0, 0, 0, 0.5);
      height: 50vh;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
      text-align: center;
    }
    .hero h1 {
      font-size: 2.5rem;
      background: rgba(0,0,0,0.6);
      padding: 1rem 2rem;
      border-radius: 10px;
    }
    .section {
      max-width: 1200px;
      margin: 2rem auto;
      padding: 0 2rem;
      background: white;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.2);
    }
    .section h2 {
      margin-bottom: 1rem;
    }
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 1.5rem;
    }
    .product-card {
      background: white;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      overflow: hidden;
      transition: transform 0.2s;
    }
    .product-card:hover {
      transform: translateY(-5px);
    }
    .product-card img {
      width: 100%;
      height: 180px;
      object-fit: cover;
    }
    .product-info {
      padding: 1rem;
    }
    .product-info h4 {
      margin: 0.5rem 0;
    }
    .product-info p {
      color: #666;
      font-size: 0.9rem;
    }
    .upload-form {
      margin-top: 2rem;
    }
    .upload-form label {
      display: block;
      margin-bottom: 0.5rem;
    }
    .upload-form input[type="text"],
    .upload-form input[type="number"],
    .upload-form input[type="url"] {
      padding: 0.5rem;
      width: 100%;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .upload-form input[type="file"] {
      margin-bottom: 1rem;
    }
    .upload-form button {
      background: #ff6600;
      color: white;
      padding: 0.6rem 1.2rem;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    footer {
      background: #000;
      color: white;
      padding: 2rem;
      text-align: center;
      margin-top: 3rem;
    }
    footer a {
      color: #ff6600;
      margin: 0 0.5rem;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <header>
    <div><strong>Promota</strong></div>
    <nav>
      <a href="#">Home</a>
      <a href="#">Men</a>
      <a href="#">Women</a>
      <a href="#">Kids</a>
      <a href="#upload">Settings</a>
    </nav>
  </header>

  <div class="hero">
    <h1>Men's Collection</h1>
  </div>

  <div class="section">
    <h2>Explore Our Best Picks</h2>
    <div class="products" id="product-list">
      <div class="product-card">
        <img src="https://images.unsplash.com/photo-1606813902786-f5d1e44d06f3" alt="Black Formal">
        <div class="product-info">
          <h4>Black Leather Formal</h4>
          <p>₹4,099</p>
        </div>
      </div>
      <div class="product-card">
        <img src="https://images.unsplash.com/photo-1587668173629-d6e0f12a4a58" alt="Men Sneaker">
        <div class="product-info">
          <h4>White Street Sneaker</h4>
          <p>₹2,799</p>
        </div>
      </div>
      <div class="product-card">
        <img src="https://images.unsplash.com/photo-1528701800484-3c8b2640c2d2" alt="Boots">
        <div class="product-info">
          <h4>Brown Hiking Boots</h4>
          <p>₹3,599</p>
        </div>
      </div>
    </div>

    <div class="upload-form" id="upload">
      <h2>Upload New Product</h2>
      <form id="product-form">
        <label for="product-name">Product Name:</label>
        <input type="text" id="product-name" name="product-name" required>

        <label for="product-price">Price (₹):</label>
        <input type="number" id="product-price" name="product-price" required>

        <label for="product-image">Image URL:</label>
        <input type="url" id="product-image" name="product-image">

        <label for="upload-file">Or Upload Image File:</label>
        <input type="file" id="upload-file" accept="image/*">

        <button type="submit">Upload</button>
      </form>
    </div>
  </div>

  <footer>
    <p>&copy; 2025 Promota. All rights reserved.</p>
    <p>
      <a href="#">Privacy Policy</a> |
      <a href="#">Terms of Service</a> |
      <a href="#">Contact</a>
    </p>
  </footer>

  <script>
    document.getElementById('product-form').addEventListener('submit', function(event) {
      event.preventDefault();

      const name = document.getElementById('product-name').value;
      const price = document.getElementById('product-price').value;
      const imageURL = document.getElementById('product-image').value;
      const fileInput = document.getElementById('upload-file');

      if (fileInput.files.length > 0) {
        const reader = new FileReader();
        reader.onload = function(e) {
          createProductCard(name, price, e.target.result);
        };
        reader.readAsDataURL(fileInput.files[0]);
      } else {
        createProductCard(name, price, imageURL);
      }

      document.getElementById('product-form').reset();
    });

    function createProductCard(name, price, image) {
      const card = document.createElement('div');
      card.className = 'product-card';
      card.innerHTML = `
        <img src="${image}" alt="${name}">
        <div class="product-info">
          <h4>${name}</h4>
          <p>₹${price}</p>
        </div>
      `;
      document.getElementById('product-list').appendChild(card);
    }
  </script>
</body>
grfg4g44gf
