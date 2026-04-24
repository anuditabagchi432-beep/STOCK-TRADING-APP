# STOCK-TRADING-APP

STOCK TRADING APP IN WEB DEVELOPMENT

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ProTrader Dashboard</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .stock-up { color: #10b981; }
        .stock-down { color: #ef4444; }
    </style>
</head>
<body class="bg-gray-900 text-white font-sans">

    <nav class="p-4 border-b border-gray-700 flex justify-between items-center">
        <h1 class="text-xl font-bold">ProTrader<span class="text-blue-500">.io</span></h1>
        <div class="space-x-4">
            <span class="text-gray-400">Balance: $24,500.00</span>
            <button class="bg-blue-600 px-4 py-2 rounded">Deposit</button>
        </div>
    </nav>

    <main class="p-6 grid grid-cols-1 md:grid-cols-3 gap-6">
        <div class="col-span-2 bg-gray-800 p-6 rounded-lg">
            <h2 class="text-lg font-semibold mb-4">Market Overview</h2>
            <table class="w-full text-left">
                <thead><tr class="text-gray-400 border-b border-gray-700"><th>Symbol</th><th>Price</th><th>Change</th><th>Action</th></tr></thead>
                <tbody id="stock-table">
                    </tbody>
            </table>
        </div>

        <div class="bg-gray-800 p-6 rounded-lg">
            <h2 class="text-lg font-semibold mb-4">Place Order</h2>
            <input type="text" placeholder="Ticker (e.g. AAPL)" class="w-full p-2 mb-3 bg-gray-700 rounded text-white">
            <input type="number" placeholder="Quantity" class="w-full p-2 mb-3 bg-gray-700 rounded text-white">
            <div class="flex gap-2">
                <button class="w-1/2 bg-green-600 py-2 rounded">BUY</button>
                <button class="w-1/2 bg-red-600 py-2 rounded">SELL</button>
            </div>
        </div>
    </main>

    <script>
        const stocks = [
            { symbol: 'AAPL', price: 175.20, change: '+1.2%' },
            { symbol: 'TSLA', price: 165.40, change: '-0.5%' },
            { symbol: 'BTC', price: 62400.00, change: '+2.4%' },
            { symbol: 'NVDA', price: 880.15, change: '+3.1%' }
        ];

        function renderStocks() {
            const container = document.getElementById('stock-table');
            container.innerHTML = stocks.map(s => `
                <tr class="border-b border-gray-700">
                    <td class="py-3 font-bold">${s.symbol}</td>
                    <td>$${s.price.toLocaleString()}</td>
                    <td class="${s.change.includes('+') ? 'stock-up' : 'stock-down'}">${s.change}</td>
                    <td><button class="text-blue-400 hover:underline">Trade</button></td>
                </tr>
            `).join('');
        }
        renderStocks();
    </script>
</body>
</html>
