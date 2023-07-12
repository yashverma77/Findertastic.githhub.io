
<html>
<head>
  <title>College Finder</title>
  <style>
    /* Add some basic styling */
    body {
      font-family: Arial, sans-serif;
      background-color: #AAC001;
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
    <label for="college">College:</label>
    <select id="college" name="college">
      <option value="">All</option>
      <option value="college-a">engineering college</option>
      <option value="college-b">medical College </option>
      <option value="college-c"> Commerce College </option>
      <option value="college-d"> Arts college </option>
      <option value="college-e"> Music And dance college </option>
      <option value="college-f"> Cinema and entertainment college </option>
      <!-- Add more options as needed -->
    </select>
    <br>
    <label for="course">Course:</label>
    <select id="course" name="course">
      <option value="">All</option>
      <option value="engineering">B-Tech</option>
      <option value="medical">MBBS</option>
      <option value="commerce">BBA</option>
      <option value="art">BA</option>
      <option value="music and dance"> Classical dance</option>
      <option value="cinema and entertainment"> Acting skills </option>
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
      <option value="Chennai"> Chennai</option>
      <option value="Chandigarh"> Chandigarh</option>
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
        { name: 'Engineering College ', course: 'B-Tech', location: 'Delhi' },
        { name: 'Medical College ', course: 'MBBS', location: 'Mumbai' },
        { name: 'Commerce College ', course: 'BBA', location: 'Noida' },
        {name: 'ARTS College', course:'BA' ,location: 'Bangalore'},
        {name: 'music and dance college', course:'Classical dance' , location: 'Chennai'},
        {name: 'cinema college', course:'Acting skills', location:'Chandigarh'},
      ];

      // Apply filters based on the selected options
      if (college) {
        colleges = colleges.filter(collegeObj = collegeObj.name.toLowerCase() === college.toLowerCase());
      }
      if (course) {
        colleges = colleges.filter(collegeObj = collegeObj.course.toLowerCase() === course.toLowerCase());
      }
      if (location) {
        colleges = colleges.filter(collegeObj = collegeObj.location.toLowerCase() === location.toLowerCase());
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
