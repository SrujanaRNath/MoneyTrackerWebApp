# MoneyTrackerWebApp
HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Money Tracker</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <div class="container">
        <h1>Money Tracker</h1>
        
        <div class="form-container">
            <h2>Add Transaction</h2>
            <form id="transaction-form">
                <label for="type">Type:</label>
                <select id="type" name="type" required>
                    <option value="income">Income</option>
                    <option value="expense">Expense</option>
                </select>
                
                <label for="description">Description:</label>
                <input type="text" id="description" name="description" placeholder="Description" required>
                
                <label for="amount">Amount:</label>
                <input type="number" id="amount" name="amount" placeholder="Amount" required>
                
                <button type="submit">Add Transaction</button>
            </form>
        </div>
        
        <div class="transactions-container">
            <h2>Transactions</h2>
            <table id="transactions-table">
                <thead>
                    <tr>
                        <th>Type</th>
                        <th>Description</th>
                        <th>Amount</th>
                    </tr>
                </thead>
                <tbody>
                    <!-- Transactions will be inserted here -->
                </tbody>
            </table>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>



CSS(styles.css)
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
}

.container {
    width: 80%;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-radius: 8px;
}

h1 {
    text-align: center;
    color: #333;
}

.form-container, .transactions-container {
    margin-bottom: 20px;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin-top: 10px;
    color: #555;
}

input, select {
    padding: 10px;
    margin-top: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    margin-top: 10px;
    padding: 10px;
    background-color: #5cb85c;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #4cae4c;
}

table {
    width: 100%;
    border-collapse: collapse;
}

th, td {
    padding: 10px;
    border-bottom: 1px solid #ddd;
    text-align: left;
}

th {
    background-color: #f4f4f4;
}

JavaScript(script.js)
document.getElementById('transaction-form').addEventListener('submit', function(event) {
    event.preventDefault();
    
    const type = document.getElementById('type').value;
    const description = document.getElementById('description').value;
    const amount = parseFloat(document.getElementById('amount').value).toFixed(2);
    
    if (description && amount) {
        const tableBody = document.getElementById('transactions-table').getElementsByTagName('tbody')[0];
        const row = tableBody.insertRow();
        
        row.insertCell(0).textContent = type.charAt(0).toUpperCase() + type.slice(1);
        row.insertCell(1).textContent = description;
        row.insertCell(2).textContent = `$${amount}`;
        
        // Clear form fields
        document.getElementById('transaction-form').reset();
    }
});
