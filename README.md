# sports-card-shop
-<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sports Card Shop</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #151515;
    color: white;
    text-align: center;
}

header {
    background: #242424;
    padding: 15px;
}

h1 {
    margin: 5px;
}

.stats {
    display: flex;
    justify-content: space-around;
    background: #303030;
    padding: 12px;
}

.shop {
    padding: 20px;
}

.shelf {
    background: #6b4226;
    padding: 20px;
    margin: 20px auto;
    max-width: 400px;
    border-radius: 12px;
}

.pack {
    background: white;
    color: black;
    padding: 15px;
    margin: 10px;
    border-radius: 10px;
}

button {
    padding: 12px 20px;
    border: none;
    border-radius: 8px;
    background: #2196f3;
    color: white;
    font-size: 16px;
    margin: 5px;
}

button:active {
    transform: scale(.95);
}

.customer {
    background: #292929;
    padding: 15px;
    margin: 10px auto;
    max-width: 350px;
    border-radius: 10px;
}
</style>
</head>

<body>

<header>
<h1>🏪 Logan's Card Shop</h1>
<p>Sports Card Shop Simulator</p>
</header>

<div class="stats">
<div>💵 $<span id="money">100</span></div>
<div>📦 Packs: <span id="packs">0</span></div>
<div>⭐ Level: <span id="level">1</span></div>
</div>

<div class="shop">

<h2>📦 Supplier</h2>

<button onclick="buyPacks()">
Buy 5 Packs - $25
</button>

<h2>🗄️ Your Shelf</h2>

<div class="shelf">

<div class="pack">
🏈 Football Pack
<br>
$8
<br>
<button onclick="sellPack()">Sell Pack</button>
</div>

</div>

<h2>👥 Customers</h2>

<div id="customers">
No customers right now...
</div>

</div>

<script>

let money = 100;
let packs = 0;
let level = 1;

function update() {
    document.getElementById("money").textContent = money;
    document.getElementById("packs").textContent = packs;
    document.getElementById("level").textContent = level;
}

function buyPacks() {

    if (money >= 25) {

        money -= 25;
        packs += 5;

        alert("You bought 5 football packs!");

        update();

    } else {

        alert("You don't have enough money!");

    }
}

function sellPack() {

    if (packs > 0) {

        packs--;
        money += 8;

        alert("Customer bought a pack for $8!");

        update();

    } else {

        alert("You don't have any packs stocked!");

    }
}

function spawnCustomer() {

    const customers = document.getElementById("customers");

    customers.innerHTML = `
        <div class="customer">
        🧑 Customer arrived!
        <br>
        They want a football pack.
        <br>
        <button onclick="sellPack()">Sell Pack for $8</button>
        </div>
    `;
}

update();

setInterval(spawnCustomer, 8000);

</script>

</body>
</html>
