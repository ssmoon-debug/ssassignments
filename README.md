<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sanjina's Assignment Tracker</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #FAF3E0;
      color: #3B3B3B;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #B5D3C3;
      padding: 20px;
      text-align: center;
      font-size: 2em;
      font-weight: bold;
    }
    .university-id {
      font-size: 0.5em;
      color: #1E6F5C;
      margin-top: 5px;
      font-weight: normal;
    }
    header img {
      max-height: 100px;
      margin-top: 10px;
    }
    #assignment-section {
      max-width: 800px;
      margin: 30px auto;
      padding: 20px;
      background-color: #ffffff;
      border-radius: 15px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
      text-align: center;
    }
    .assignment-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 20px;
      margin-top: 20px;
    }
    .assignment {
      background-color: #FAF3E0;
      padding: 20px;
      border-radius: 10px;
      text-align: center;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s, box-shadow 0.3s;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    .assignment:hover {
      transform: translateY(-5px);
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
    }
    .assignment-title {
      font-weight: bold;
      font-size: 1.2em;
      color: #1E6F5C;
      margin-bottom: 8px;
    }
    .status-indicator {
      position: absolute;
      top: 10px;
      right: 10px;
      width: 12px;
      height: 12px;
      border-radius: 50%;
    }
    .status-upcoming {
      background-color: #FFB347;
    }
    .status-in-progress {
      background-color: #4682B4;
    }
    .status-completed {
      background-color: #77DD77;
    }
    .admin-controls {
      margin-top: 12px;
      display: flex;
      justify-content: center;
      gap: 8px;
    }
    .admin-controls button {
      background-color: #B5D3C3;
      border: none;
      padding: 6px 12px;
      border-radius: 5px;
      cursor: pointer;
      font-size: 0.85em;
      transition: background-color 0.2s;
    }
    .admin-controls button:hover {
      background-color: #98C1AC;
    }
    footer {
      text-align: center;
      padding: 20px;
      background-color: #B5D3C3;
      font-size: 0.9em;
      color: #3B3B3B;
      margin-top: 40px;
    }
    input, button, select {
      padding: 10px;
      margin: 5px;
      border-radius: 8px;
      border: 1px solid #ddd;
      font-family: inherit;
    }
    #add-btn, #admin-btn, #exit-admin-btn {
      background-color: #1E6F5C;
      color: white;
      border: none;
      cursor: pointer;
      font-weight: bold;
      padding: 12px 20px;
      transition: background-color 0.3s;
    }
    #add-btn:hover, #admin-btn:hover, #exit-admin-btn:hover {
      background-color: #18594A;
    }
    #admin-form {
      background-color: #f9f9f9;
      padding: 20px;
      border-radius: 10px;
      margin: 20px 0;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
    }
    .form-group {
      margin-bottom: 10px;
    }
    h2 {
      color: #1E6F5C;
      margin-bottom: 20px;
      position: relative;
      display: inline-block;
    }
    h2:after {
      content: "";
      position: absolute;
      width: 60%;
      height: 3px;
      background-color: #B5D3C3;
      bottom: -10px;
      left: 20%;
    }
    .search-filter {
      margin: 20px 0;
      display: flex;
      justify-content: center;
      gap: 10px;
      flex-wrap: wrap;
    }
    #search-input {
      flex-grow: 1;
      max-width: 300px;
    }
    .status-filter {
      padding: 8px 15px;
      background-color: #FAF3E0;
      border-radius: 20px;
      cursor: pointer;
      transition: background-color 0.2s;
    }
    .status-filter.active {
      background-color: #B5D3C3;
      font-weight: bold;
    }
    .progress-tracker {
      background-color: #f3f3f3;
      border-radius: 10px;
      padding: 15px;
      margin: 20px 0;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
    }
    .progress-bar {
      display: flex;
      margin: 15px 0;
      height: 20px;
      border-radius: 10px;
      overflow: hidden;
    }
    .progress-segment {
      height: 100%;
      transition: width 0.5s ease;
    }
    .progress-completed {
      background-color: #77DD77;
    }
    .progress-in-progress {
      background-color: #4682B4;
    }
    .progress-upcoming {
      background-color: #FFB347;
    }
    .progress-stats {
      display: flex;
      justify-content: space-around;
      margin-top: 10px;
    }
    .progress-item {
      display: flex;
      align-items: center;
      font-size: 0.9em;
    }
    .progress-dot {
      width: 10px;
      height: 10px;
      border-radius: 50%;
      margin-right: 5px;
    }
    .button-container {
  display: flex;
  justify-content: center;
  gap: 15px;
  margin: 20px 0;
}

#crypto-tool-btn {
  background-color: #1E6F5C;
  color: white;
  border: none;
  cursor: pointer;
  font-weight: bold;
  padding: 12px 20px;
  border-radius: 8px;
  transition: background-color 0.3s;
}

#crypto-tool-btn:hover {
  background-color: #18594A;
}
</style>
</head>
<body>
  <header>
    Sanjina's Assignments 🐾<br>
    <div class="university-id">2417503 - Dong-A University</div>
    <img src="https://upload.wikimedia.org/wikipedia/en/5/53/Snoopy_Peanuts.png" alt="Snoopy" />
    <div style="font-size: 0.5em; color: #1E6F5C; text-decoration: underline; cursor: pointer; margin-top: 5px;" onclick="window.open('grades.html', '_blank')">
  View Grades
</div>

  </header>

  <div id="assignment-section">
    <h2>My Assignments</h2>
    
    <div class="progress-tracker">
      <h3>Progress Overview</h3>
      <div class="progress-bar">
        <div class="progress-segment progress-completed" id="completed-bar"></div>
        <div class="progress-segment progress-in-progress" id="in-progress-bar"></div>
        <div class="progress-segment progress-upcoming" id="upcoming-bar"></div>
      </div>
      <div class="progress-stats">
        <div class="progress-item">
          <div class="progress-dot progress-completed"></div>
          <span id="completed-count">0 Completed</span>
        </div>
        <div class="progress-item">
          <div class="progress-dot progress-in-progress"></div>
          <span id="in-progress-count">0 In Progress</span>
        </div>
        <div class="progress-item">
          <div class="progress-dot progress-upcoming"></div>
          <span id="upcoming-count">0 Upcoming</span>
        </div>
      </div>
    </div>
    
    <div class="search-filter">
      <input type="text" id="search-input" placeholder="Search assignments..." />
      <div class="status-filter active" data-status="all">All</div>
      <div class="status-filter" data-status="upcoming">Upcoming</div>
      <div class="status-filter" data-status="in-progress">In Progress</div>
      <div class="status-filter" data-status="completed">Completed</div>
    </div>
    
       
    <div class="button-container">
  <button id="admin-btn">Enter Admin Mode</button>
  <button id="crypto-tool-btn" onclick="window.open('https://ssmoon-debug.github.io/GGCryptographytool/')">Cryptography Tool</button>
  <button id="exit-admin-btn" style="display: none;">Exit Admin Mode</button>
</div>
    
    <div id="admin-form" style="display: none;">
      <div class="form-group">
        <input type="text" id="assignment-input" placeholder="Assignment name" />
      </div>
      <div class="form-group">
        <input type="url" id="link-input" placeholder="Assignment URL" />
      </div>
      <div class="form-group">
        <select id="status-input">
          <option value="upcoming">Upcoming</option>
          <option value="in-progress">In Progress</option>
          <option value="completed">Completed</option>
        </select>
      </div>
      <button id="add-btn">Add Assignment</button>
    </div>

    <div id="assignments" class="assignment-grid"></div>
  </div>

  <footer>
    <div>© 2025 Sanjina. All rights reserved.</div>
    <div style="margin-top: 10px;">Life is good.</div>
  </footer>

  <script>
    const password = "starsandsaturn";
    let isAdmin = false;
    let currentFilter = "all";

    const assignmentInput = document.getElementById("assignment-input");
    const linkInput = document.getElementById("link-input");
    const statusInput = document.getElementById("status-input");
    const searchInput = document.getElementById("search-input");
    const assignmentsDiv = document.getElementById("assignments");
    const adminBtn = document.getElementById("admin-btn");
    const exitAdminBtn = document.getElementById("exit-admin-btn");
    const adminForm = document.getElementById("admin-form");
    const statusFilters = document.querySelectorAll(".status-filter");

    // Progress tracking elements
    const completedBar = document.getElementById("completed-bar");
    const inProgressBar = document.getElementById("in-progress-bar");
    const upcomingBar = document.getElementById("upcoming-bar");
    const completedCount = document.getElementById("completed-count");
    const inProgressCount = document.getElementById("in-progress-count");
    const upcomingCount = document.getElementById("upcoming-count");

    // Pre-defined assignments with updated statuses as requested
    const initialAssignments = [
      { name: "Identity Verification", url: "https://ssmoon-debug.github.io/assignment-1/", status: "completed" },
      { name: "CLI Dungeon Crawl", url: "https://ssmoon-debug.github.io/assignment-2/", status: "completed" },
      { name: "Virtual Library", url: "https://ssmoon-debug.github.io/assignment-3/", status: "completed" },
      { name: "Assignment 4", url: "https://example.com/assignment4", status: "in-progress" },
      { name: "Cryptography Project", url: "https://ssmoon-debug.github.io/Cryptography/", status: "completed" },
      { name: "HIF-Lumen", url: "https://ssmoon-debug.github.io/HIF-Lumen/", status: "completed" },
      { name: "Assignment 7", url: "https://example.com/assignment7", status: "upcoming" },
      { name: "Assignment 8", url: "https://example.com/assignment8", status: "upcoming" },
      { name: "Assignment 9", url: "https://example.com/assignment9", status: "upcoming" },
      { name: "Assignment 10", url: "https://example.com/assignment10", status: "upcoming" }
    ];

    async function loadAssignments() {
      try {
        const response = await fetch('https://api.npoint.io/7c19cf4022061ea268b0');
        return await response.json();
      } catch (error) {
        console.error("Could not load assignments from API, using initial data:", error);
        return initialAssignments;
      }
    }

    async function saveAssignments(assignments) {
      try {
        await fetch('https://api.npoint.io/7c19cf4022061ea268b0', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(assignments)
        });
      } catch (error) {
        console.error("Could not save assignments to API:", error);
        alert("Could not save changes. Please try again later.");
      }
    }

    let savedAssignments = [];

    function updateProgressTracker() {
      // Count assignments by status
      const counts = {
        completed: savedAssignments.filter(a => a.status === "completed").length,
        inProgress: savedAssignments.filter(a => a.status === "in-progress").length,
        upcoming: savedAssignments.filter(a => a.status === "upcoming").length
      };
      
      const total = counts.completed + counts.inProgress + counts.upcoming;
      
      // Update count text
      completedCount.textContent = `${counts.completed} Completed`;
      inProgressCount.textContent = `${counts.inProgress} In Progress`;
      upcomingCount.textContent = `${counts.upcoming} Upcoming`;
      
      // Calculate percentages for progress bar (avoid division by zero)
      if (total > 0) {
        completedBar.style.width = `${(counts.completed / total) * 100}%`;
        inProgressBar.style.width = `${(counts.inProgress / total) * 100}%`;
        upcomingBar.style.width = `${(counts.upcoming / total) * 100}%`;
      } else {
        completedBar.style.width = "0%";
        inProgressBar.style.width = "0%";
        upcomingBar.style.width = "0%";
      }
    }

    async function initialize() {
      savedAssignments = await loadAssignments();
      // Add status if not present in loaded data and convert old "new" status to "upcoming"
      savedAssignments = savedAssignments.map(a => {
        let status = a.status || "upcoming";
        // Convert old "new" status to "upcoming"
        if (status === "new") {
          status = "upcoming";
        }
        return {
          ...a,
          status: status
        };
      });
      
      if (savedAssignments.length === 0) {
        savedAssignments = initialAssignments;
        await saveAssignments(savedAssignments);
      }
      
      updateProgressTracker();
      renderAssignments(savedAssignments);
    }

    document.getElementById("add-btn").onclick = async () => {
      const name = assignmentInput.value.trim();
      const url = linkInput.value.trim();
      const status = statusInput.value;
      
      if (!name || !url) {
        alert("Please enter assignment name and URL");
        return;
      }
      
      const newAssignment = { name, url, status };
      savedAssignments.push(newAssignment);
      await saveAssignments(savedAssignments);
      updateProgressTracker();
      renderAssignments(savedAssignments);
      
      assignmentInput.value = "";
      linkInput.value = "";
    };

    function filterAssignments() {
      const searchTerm = searchInput.value.toLowerCase();
      let filtered = savedAssignments;
      
      // Apply status filter
      if (currentFilter !== "all") {
        filtered = filtered.filter(a => a.status === currentFilter);
      }
      
      // Apply search term
      if (searchTerm) {
        filtered = filtered.filter(a => a.name.toLowerCase().includes(searchTerm));
      }
      
      renderAssignments(filtered);
    }

    function renderAssignments(list) {
      assignmentsDiv.innerHTML = "";
      list.forEach((a, index) => {
        const div = document.createElement("div");
        div.className = "assignment";
        div.onclick = () => {
          if (!isAdmin) {
            window.open(a.url, '_blank');
          }
        };

        const title = document.createElement("div");
        title.className = "assignment-title";
        title.textContent = a.name;
        
        const statusIndicator = document.createElement("div");
        statusIndicator.className = `status-indicator status-${a.status}`;
        
        div.appendChild(statusIndicator);
        div.appendChild(title);

        if (isAdmin) {
          const adminDiv = document.createElement("div");
          adminDiv.className = "admin-controls";

          const editUrlBtn = document.createElement("button");
          editUrlBtn.textContent = "Edit URL";
          editUrlBtn.onclick = async (e) => {
            e.stopPropagation();
            const newUrl = prompt("Edit assignment URL:", a.url);
            if (newUrl) {
              a.url = newUrl;
              await saveAssignments(savedAssignments);
              filterAssignments();
            }
          };

          const renameBtn = document.createElement("button");
          renameBtn.textContent = "Rename";
          renameBtn.onclick = async (e) => {
            e.stopPropagation();
            const newName = prompt("Rename assignment:", a.name);
            if (newName) {
              a.name = newName;
              await saveAssignments(savedAssignments);
              filterAssignments();
            }
          };
          
          const statusBtn = document.createElement("button");
          statusBtn.textContent = "Change Status";
          statusBtn.onclick = async (e) => {
            e.stopPropagation();
            const statuses = ["upcoming", "in-progress", "completed"];
            const currentIndex = statuses.indexOf(a.status);
            const nextIndex = (currentIndex + 1) % statuses.length;
            a.status = statuses[nextIndex];
            await saveAssignments(savedAssignments);
            updateProgressTracker();
            filterAssignments();
          };

          const deleteBtn = document.createElement("button");
          deleteBtn.textContent = "Delete";
          deleteBtn.onclick = async (e) => {
            e.stopPropagation();
            if (confirm("Delete this assignment?")) {
              const origIndex = savedAssignments.findIndex(item => 
                item.name === a.name && item.url === a.url);
              if (origIndex !== -1) {
                savedAssignments.splice(origIndex, 1);
                await saveAssignments(savedAssignments);
                updateProgressTracker();
                filterAssignments();
              }
            }
          };

          adminDiv.appendChild(renameBtn);
          adminDiv.appendChild(editUrlBtn);
          adminDiv.appendChild(statusBtn);
          adminDiv.appendChild(deleteBtn);
          div.appendChild(adminDiv);
        }

        assignmentsDiv.appendChild(div);
      });
    }

    adminBtn.onclick = () => {
      const input = prompt("Enter admin password:");
      if (input === password) {
        isAdmin = true;
        adminForm.style.display = "block";
        adminBtn.style.display = "none";
        exitAdminBtn.style.display = "inline-block";
        filterAssignments();
      }
    };

    exitAdminBtn.onclick = () => {
      isAdmin = false;
      adminForm.style.display = "none";
      adminBtn.style.display = "inline-block";
      exitAdminBtn.style.display = "none";
      filterAssignments();
    };
    
    // Add event listeners for filters
    statusFilters.forEach(filter => {
      filter.addEventListener("click", () => {
        statusFilters.forEach(f => f.classList.remove("active"));
        filter.classList.add("active");
        currentFilter = filter.dataset.status;
        filterAssignments();
      });
    });
    
    // Add event listener for search
    searchInput.addEventListener("input", filterAssignments);

    initialize();
  </script>
</body>
</html>
