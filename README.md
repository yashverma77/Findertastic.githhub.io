<!DOCTYPE html>
<html>
<head>
  <title>College Finder</title>
  <style>
    /* Add some basic styling */
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      margin: 0;
      padding: 20px;
    }
    h1 {
      text-align: center;
    }
    form {
      margin-bottom: 20px;
    }
    label {
      font-weight: bold;
    }
    select, button {
      padding: 6px;
      font-size: 16px;
      border-radius: 4px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #4CAF50;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      background-color: white;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    th, td {
      padding: 12px;
      text-align: left;
      border-bottom: 1px solid #ddd;
    }
    th {
      background-color: #333;
      color: white;
    }
    tr:nth-child(even) {
      background-color: #f2f2f2;
    }
  </style>
</head>
<body>
  <h1>College Finder</h1>
  <form id="search-form">
    <label for="COLLEGE">COLLEGE:</label>
    <select id="COLLEGE" name="COLLEGE">
      <option value="">All</option>
      <option value="Engineering College"> Engineering College </option>
      <option value=" Medical College "> Medical College </option>
      <option value="ARTS College"> ARTS College </option>
      <option value="Commerce College "> Commerce College </option>
      <!-- Add more options as needed -->
    </select>
    <br>
    <label for="COURSE">COURSE:</label>
    <select id="COURSE" name="COURSE">
      <option value="">All</option>
      <option value="engineering">B-Tech</option>
      <option value="medical">MBBS</option>
      <option value="commerce">BBA</option>
      <option value="art">BA</option>
      <!-- Add more options as needed -->
    </select>
    <br>
    <label for="location">Location:</label>
    <select id="location" name="location">
      <option value="">All</option>
      <option value="delhi">Delhi</option>
      <option value="mumbai">Mumbai</option>
      <option value="noida">Noida</option>
      <option value="bangalore">Bangalore</option>
      <!-- Add more options as needed -->
    </select>
    <br>
    <button type="submit">Search</button>
  </form>
  <div id="college-data">
    <!-- College data will be populated here -->
    <table id="college-table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Course</th>
          <th>Location</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </div>

  <script>
    const searchForm = document.getElementById('search-form');
    const collegeTable = document.getElementById('college-table');

    searchForm.addEventListener('submit', function(event) {
      event.preventDefault(); // Prevent form submission

      const college = document.getElementById('college').value;
      const course = document.getElementById('course').value;
      const location = document.getElementById('location').value;

      // Call a function or make an AJAX request to fetch the college data based on the selected options
      // Example:
      const colleges = getColleges(college, course, location);

      // Render the college data in the table
      renderColleges(colleges);
    });

    function getColleges(college, course, location) {
      // This is a placeholder function, replace it with your actual logic to fetch the college data
      // You can make an AJAX request to your server or use any other method to retrieve the data
      // Return an array of college objects with name, course, and location properties
      // Example:
      const colleges = [
        { name: 'Engineering College', course: 'B-Tech', location: 'Delhi' },
        { name: 'Medical college', course: 'MBBS', location: 'Mumbai' },
        { name: 'Commerce college', course: 'BBA', location: 'Noida' },
         { name: 'ARTS college', course: 'BA', location: 'Bangalore' },
      ];

      // Apply filters based on the selected options
      if (college) {
        colleges = colleges.filter(collegeObj => collegeObj.name.toLowerCase() === college.toLowerCase());
      }
      if (course) {
        colleges = colleges.filter(collegeObj => collegeObj.course.toLowerCase() === course.toLowerCase());
      }
      if (location) {
        colleges = colleges.filter(collegeObj => collegeObj.location.toLowerCase() === location.toLowerCase());
      }

      return colleges;
    }

    function renderColleges(colleges) {
      const tbody = collegeTable.querySelector('tbody');
      tbody.innerHTML = '';

      colleges.forEach(college => {
        const row = document.createElement('tr');
        row.innerHTML = `<td>${college.name}</td><td>${college.course}</td><td>${college.location}</td>`;
        tbody.appendChild(row);
      });
    }
  </script>
</body>
</html>
