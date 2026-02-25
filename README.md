<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PropEase | Property Management SaaS</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f4f6f9;
}

header {
  background: #1e293b;
  color: white;
  padding: 30px;
  text-align: center;
}

section {
  padding: 30px;
  max-width: 1000px;
  margin: auto;
}

.card {
  background: white;
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}

input {
  padding: 8px;
  margin: 5px;
  width: 150px;
}

button {
  padding: 10px 15px;
  background: #2563eb;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background: #1d4ed8;
}

ul {
  padding-left: 20px;
}

.dashboard {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
</style>
</head>

<body>

<header>
<h1>PropEase</h1>
<p>Property Management Made Simple</p>
</header>

<section>

<div class="card">
<h2>About PropEase</h2>
<p>
PropEase helps landlords track rent income, expenses, and maintenance requests 
in one organised dashboard.
</p>
</div>

<div class="dashboard">

<div class="card">
<h2>💰 Rent Tracker</h2>
<input type="number" id="rentAmount" placeholder="Monthly Rent (£)">
<input type="number" id="months" placeholder="Months">
<br>
<button onclick="calculateRent()">Calculate</button>
<p id="rentResult"></p>
</div>

<div class="card">
<h2>🧾 Expense Tracker</h2>
<input type="text" id="expenseName" placeholder="Expense Name">
<input type="number" id="expenseAmount" placeholder="Amount (£)">
<br>
<button onclick="addExpense()">Add Expense</button>
<ul id="expenseList"></ul>
<p><strong>Total: £<span id="expenseTotal">0</span></strong></p>
</div>

<div class="card">
<h2>🛠 Maintenance Requests</h2>
<input type="text" id="maintenanceText" placeholder="Issue Description">
<br>
<button onclick="addMaintenance()">Add Request</button>
<ul id="maintenanceList"></ul>
</div>

</div>

</section>

<footer style="text-align:center; padding:20px; background:#e2e8f0;">
© 2026 PropEase | Built by Jaskaran Daudher
</footer>

<script>

let totalExpenses = 0;

function calculateRent() {
  const rent = parseFloat(document.getElementById("rentAmount").value);
  const months = parseFloat(document.getElementById("months").value);

  if (!rent || !months) {
    document.getElementById("rentResult").innerText = "Please enter valid numbers.";
    return;
  }

  const total = rent * months;
  document.getElementById("rentResult").innerText = "Total Income: £" + total;
}

function addExpense() {
  const name = document.getElementById("expenseName").value;
  const amount = parseFloat(document.getElementById("expenseAmount").value);

  if (!name || !amount) return;

  const li = document.createElement("li");
  li.innerText = name + " - £" + amount;
  document.getElementById("expenseList").appendChild(li);

  totalExpenses += amount;
  document.getElementById("expenseTotal").innerText = totalExpenses;

  document.getElementById("expenseName").value = "";
  document.getElementById("expenseAmount").value = "";
}

function addMaintenance() {
  const text = document.getElementById("maintenanceText").value;
  if (!text) return;

  const li = document.createElement("li");
  li.innerText = text;
  document.getElementById("maintenanceList").appendChild(li);

  document.getElementById("maintenanceText").value = "";
}

</script>

</body>
</html>
