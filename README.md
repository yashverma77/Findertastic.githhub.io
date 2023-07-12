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
    <label for="course">Course:</label>
    <select id="course" name="course">
      <option value="">All</option>
      <option value="engineering">Engineering</option>
      <option value="medical">Medical</option>
      <option value="commerce">Commerce</option>
      <option value="art">Art</option>
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
  </div>

  <script>
    const searchForm = document.getElementById('search-form');
    const collegeData = document.getElementById('college-data');

    searchForm.addEventListener('submit', function(event) {
      event.preventDefault(); // Prevent form submission

      const course = document.getElementById('course').value;
      const location = document.getElementById('location').value;

      // Call a function or make an AJAX request to fetch the college data based on course and location
      // Example:
      const colleges = getColleges(course, location);

      // Render the college data in the table
      renderColleges(colleges);
    });

    function getColleges(course, location) {
      // This is a placeholder function, replace it with your actual logic to fetch the college data
      // You can make an AJAX request to your server or use any other method to retrieve the data
      // Return an array of college objects with name, course, and location properties
      // Example:
      const colleges = [
        { name: 'College A', course: 'Engineering', location: 'Delhi' },
        { name: 'College B', course: 'Medical', location: 'Mumbai' },
        { name: 'College C', course: 'Commerce', location: 'Noida' },
      ];

      // Apply filters based on course and location
      if (course) {
        colleges = colleges.filter(college => college.course === course);
      }
      if (location) {
        colleges = colleges.filter(college => college.location === location);
      }

      return colleges;
    }

    function renderColleges(colleges) {
      let html = '<table>';
      html += '<tr><th>Name</th><th>Course</th><th>Location</th></tr>';
      colleges.forEach(college => {
        html += `<tr><td>${college.name}</td><td>${college.course}</td><td>${college.location}</td></tr>`;
      });
      html += '</table>';

      collegeData.innerHTML = html;
    }
  </script>
</body>
</html>
