<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Daily Revenue Tracker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f0f0f0;
        }
        h1 {
            color: #333;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        table, th, td {
            border: 1px solid #ccc;
        }
        th, td {
            padding: 10px;
            text-align: right;
        }
        th {
            background-color: #f9f9f9;
        }
    </style>
</head>
<body>
    <h1>Daily Revenue Tracker</h1>
    <table>
        <thead>
            <tr>
                <th>Day</th>
                <th>Total Revenue (Taka)</th>
            </tr>
        </thead>
        <tbody id="revenueTableBody">
            <!-- Revenue data will be inserted here -->
        </tbody>
    </table>

    <script>
        const initialInvestment = 5000;
        const dailyInterestRate = 0.01;
        const startDate = new Date('2024-06-14');

        function calculateRevenue() {
            const currentDate = new Date();
            const daysElapsed = Math.floor((currentDate - startDate) / (1000 * 60 * 60 * 24));
            
            let tableBody = document.getElementById('revenueTableBody');
            tableBody.innerHTML = ''; // Clear previous results

            let totalRevenue = initialInvestment;

            for (let day = 1; day <= daysElapsed; day++) {
                totalRevenue += totalRevenue * dailyInterestRate;
                let row = tableBody.insertRow();
                let cellDay = row.insertCell(0);
                let cellRevenue = row.insertCell(1);
                cellDay.textContent = day;
                cellRevenue.textContent = totalRevenue.toFixed(2);
            }
        }

        window.onload = function() {
            calculateRevenue();
        }
    </script>
</body>
</html>
