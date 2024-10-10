<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Taxtchin Fleet Management</title>
  <style>
    /* CSS styles */
    table {
      width: 100%;
      border-collapse: collapse;
    }
    th, td {
      padding: 8px;
      text-align: left;
      border-bottom: 1px solid #ddd;
    }
    th {
      background-color: #f2f2f2;
    }
    input, button {
      padding: 6px 12px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
  </style>
</head>
<body>
  <h1>Taxtchin Fleet Management</h1>
  
  <h2>Add New Taxi</h2>
  <form id="add-taxi-form">
    <label for="license-plate">License Plate:</label>
    <input type="text" id="license-plate" name="license-plate" required>
    
    <label for="driver-name">Driver Name:</label>
    <input type="text" id="driver-name" name="driver-name" required>
    
    <button type="submit">Add Taxi</button>
  </form>
  
  <h2>Taxi Fleet</h2>
  <table id="taxi-table">
    <thead>
      <tr>
        <th>License Plate</th>
        <th>Driver Name</th>
      </tr>
    </thead>
    <tbody>
      <!-- Taxi data will be added dynamically -->
    </tbody>
  </table>
  
  <script>
    const addTaxiForm = document.getElementById('add-taxi-form');
    const taxiTable = document.getElementById('taxi-table');
    const taxiData = [];

    function addTaxiToTable(licenseplate, drivername) {
      const row = document.createElement('tr');
      
      const licensePlateCell = document.createElement('td');
      licensePlateCell.textContent = licenseplate;
      row.appendChild(licensePlateCell);
      
      const driverNameCell = document.createElement('td');
      driverNameCell.textContent = drivername;
      row.appendChild(driverNameCell);
      
      taxiTable.getElementsByTagName('tbody')[0].appendChild(row);
    }

    addTaxiForm.addEventListener('submit', (event) => {
      event.preventDefault();
      
      const licensePlate = document.getElementById('license-plate').value;
      const driverName = document.getElementById('driver-name').value;
      
      addTaxiToTable(licensePlate, driverName);
      
      taxiData.push({ licensePlate, driverName });
      
      document.getElementById('license-plate').value = '';
      document.getElementById('driver-name').value = '';
    });
  </script>
</body>
</html>
