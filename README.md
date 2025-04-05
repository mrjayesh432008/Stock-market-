<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Trading Platform</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #111;
      color: #fff;
      margin: 0;
      padding: 0;
    }
    header, footer {
      background-color: #222;
      padding: 1em;
      text-align: center;
    }
    .container {
      padding: 20px;
    }
    .stock {
      padding: 10px;
      margin: 10px;
      border: 1px solid #555;
      border-radius: 8px;
      background-color: #1e1e1e;
      display: inline-block;
      width: 150px;
      cursor: pointer;
    }
    .stock:hover {
      background-color: #333;
    }
    .form-group {
      margin-bottom: 15px;
    }
    input, select, button {
      padding: 10px;
      border-radius: 5px;
      border: none;
      width: 100%;
    }
    button {
      background-color: #28a745;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background-color: #218838;
    }
    .grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
    }
    iframe {
      width: 100%;
      height: 400px;
    }
  </style>
</head>
<body>
  <header>
    <h1>Stock Trading Dashboard</h1>
    <div id="balance">Platform Balance: ₹0</div>
  </header>
  <div class="container">
    <h2>Available Stocks</h2>
    <div id="stockList" class="grid"></div>

    <h2>Buy Stock</h2>
    <div class="form-group">
      <input type="text" id="buySymbol" placeholder="Stock Symbol (e.g. BTC)" />
    </div>
    <div class="form-group">
      <input type="number" id="buyQuantity" placeholder="Quantity" />
    </div>
    <button onclick="buyStock()">Buy</button>

    <h2>Sell Stock</h2>
    <div class="form-group">
      <input type="text" id="sellSymbol" placeholder="Stock Symbol (e.g. BTC)" />
    </div>
    <div class="form-group">
      <input type="number" id="sellQuantity" placeholder="Quantity" />
    </div>
    <button onclick="sellStock()">Sell</button>

    <h2>Trading Chart</h2>
    <div id="chartContainer">
      <iframe id="chartFrame" src="https://www.tradingview.com" frameborder="0"></iframe>
    </div>

    <h2>Personal Profile</h2>
    <div>
      <p><strong>Name:</strong> Demo User</p>
      <p><strong>Email:</strong> demo@example.com</p>
    </div>

    <h2>Bank Info</h2>
    <div>
      <p><strong>Bank Name:</strong> ABC Bank</p>
      <p><strong>Account No:</strong> 123456789</p>
      <p><strong>IFSC:</strong> ABCD0001234</p>
    </div>
  </div>
  <footer>
    <p>&copy; 2025 Trading Platform</p>
  </footer>

  <script>
    const stocks = [
      { name: "Bitcoin", symbol: "BTC", price: 62000, up: true },
      { name: "BOB", symbol: "BOB", price: 520, up: false },
      { name: "Reliance", symbol: "RELIANCE", price: 2850, up: true },
      { name: "Tata Motors", symbol: "TATA", price: 980, up: false },
    ];

    const stockList = document.getElementById("stockList");
    const balanceDiv = document.getElementById("balance");

    function renderStocks() {
      stockList.innerHTML = "";
      stocks.forEach(stock => {
        const div = document.createElement("div");
        div.className = "stock";
        div.innerHTML = `
          <strong>${stock.name}</strong><br>
          ₹${stock.price} <span style="color:${stock.up ? 'green' : 'red'}">${stock.up ? '▲' : '▼'}</span>
        `;
        div.onclick = () => {
          document.getElementById("chartFrame").src = `https://www.tradingview.com/symbols/${stock.symbol}USD/`;
        };
        stockList.appendChild(div);
      });
    }

    function buyStock() {
      const symbol = document.getElementById("buySymbol").value;
      const quantity = parseInt(document.getElementById("buyQuantity").value);
      alert(`Buying ${quantity} of ${symbol}`);
    }

    function sellStock() {
      const symbol = document.getElementById("sellSymbol").value;
      const quantity = parseInt(document.getElementById("sellQuantity").value);
      alert(`Selling ${quantity} of ${symbol}`);
    }

    renderStocks();
  </script>
</body>
</html>
