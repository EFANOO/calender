# calender
git clone https://github.com/your-username/my-website.git
cd my-website
echo "<!DOCTYPE html>
<html>
<head>
    <title>My Website</title>
</head>
<body>
    <h1>Welcome to My Website</h1>
    <p>This is a simple HTML page hosted on GitHub Pages.</p>
</body>
</html>" > index.html
git add index.html
git commit -m "Add index.html"
git push
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Student AI Calendar</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    h2 { margin-top: 30px; }
    input, select, button { margin: 5px 0; padding: 8px; width: 100%; max-width: 400px; }
    .event-list, .schedule { margin-top: 20px; }
    .event-item, .schedule-item { border: 1px solid #ccc; padding: 10px; margin: 5px 0; }
  </style>
</head>
<body>
  <h1>Student AI Calendar</h1>

  <h2>Add Assignment</h2>
  <label>Assignment:</label>
  <input type="text" id="assignmentName" placeholder="e.g. Science Test" />
  <label>Due Date:</label>
  <input type="date" id="dueDate" />
  <label>Importance (1–10):</label>
  <input type="number" id="importance" min="1" max="10" />
  <label>Estimated Time (minutes):</label>
  <input type="number" id="duration" />
  <button onclick="addAssignment()">Add Assignment</button>

  <div class="event-list" id="eventList">
    <h2>Assignments</h2>
  </div>

  <h2>Daily Presets</h2>
  <label>Event:</label>
  <input type="text" id="presetEvent" placeholder="e.g. School" />
  <label>Start Time:</label>
  <input type="time" id="presetStart" />
  <label>End Time:</label>
  <input type="time" id="presetEnd" />
  <button onclick="addPreset()">Add Preset</button>

  <div class="event-list" id="presetList">
    <h2>Daily Events</h2>
  </div>

  <h2>Generate Schedule</h2>
  <button onclick="generateSchedule()">Generate</button>
  <div class="schedule" id="scheduleList">
    <h2>Today’s Schedule</h2>
  </div>

  <script>
    let assignments = [];
    let presets = [];

    function addAssignment() {
      const assignment = {
        name: document.getElementById("assignmentName").value,
        due: document.getElementById("dueDate").value,
        importance: parseInt(document.getElementById("importance").value),
        duration: parseInt(document.getElementById("duration").value)
      };
      assignments.push(assignment);
      displayAssignments();
    }

    function addPreset() {
      const preset = {
        event: document.getElementById("presetEvent").value,
        start: document.getElementById("presetStart").value,
        end: document.getElementById("presetEnd").value
      };
      presets.push(preset);
      displayPresets();
    }

    function displayAssignments() {
      const list = document.getElementById("eventList");
      list.innerHTML = "<h2>Assignments</h2>";
      assignments.forEach((a, i) => {
        list.innerHTML += `<div class="event-item">${a.name} - Due: ${a.due}, Importance: ${a.importance}, Duration: ${a.duration} min</div>`;
      });
    }

    function displayPresets() {
      const list = document.getElementById("presetList");
      list.innerHTML = "<h2>Daily Events</h2>";
      presets.forEach((p, i) => {
        list.innerHTML += `<div class="event-item">${p.event}: ${p.start} to ${p.end}</div>`;
      });
    }

    function generateSchedule() {
      const schedule = document.getElementById("scheduleList");
      schedule.innerHTML = "<h2>Today’s Schedule</h2>";
      assignments.sort((a, b) => b.importance - a.importance);
      assignments.forEach(a => {
        schedule.innerHTML += `<div class="schedule-item">${a.name} - Work for ${a.duration} minutes</div>`;
      });
    }
  </script>
</body>
</html>

