
<html>
<head>
  <title>College Finder</title>
  <style>
    /* Add some basic styling */
    body {
      font-family: Arial, sans-serif;
    }
    form {
      margin-bottom: 20px;
    }
    table {
      border-collapse: collapse;
      width: 100%;
    }
    th, td {
      padding: 8px;
      text-align: left;
      border-bottom: 1px solid #ddd;
    }
  </style>
</head>
<body>
  <h1>College Finder</h1>
  <form id="search-form">
    <label for="course">Course:</label>
    <select id="course" name="course">
      <option value="">All</option>
      <option value="engineering">Engineering</option>
      <option value="medical">Medical</option>
      <!-- Add more options as needed -->
    </select>
    <br>
    <label for="location">Location:</label>
    <select id="location" name="location">
      <option value="">All</option>
      <option value="delhi">Delhi</option>
      <option value="mumbai">Mumbai</option>
      <!-- Add more options as needed -->
    </select>
    <br>
    <button type="submit">Search</button>
    
  </form>
  <table id="college-list">
    <thead>
      <tr>
        <th>Name</th>
        <th>Course</th>
        <th>Location</th>
        <!-- Add more columns as needed -->
      </tr>
    </thead>
    <tbody>
      <!-- College data will be populated here -->
      
    </tbody>
  </table>

  <script src="script.js"></script>
</body>
</html>
