# FitnessTrackerApp
index.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fitness Tracker</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Fitness Tracker</h1>
        
        <div class="form-section">
            <h2>Record a Workout</h2>
            <form id="workout-form">
                <input type="text" id="exercise" placeholder="Exercise Name" required>
                <input type="number" id="duration" placeholder="Duration (minutes)" required>
                <input type="number" id="calories" placeholder="Calories Burned" required>
                <button type="submit">Add Workout</button>
            </form>
        </div>

        <div class="goal-section">
            <h2>Set Fitness Goal</h2>
            <input type="text" id="goal" placeholder="Your Fitness Goal">
            <button id="set-goal">Set Goal</button>
            <p id="goal-display"></p>
        </div>

        <div class="workout-list">
            <h2>Your Workouts</h2>
            <ul id="workout-list"></ul>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>

style.css
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 600px;
    margin: auto;
    background: rgb(92, 245, 207);
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1, h2 {
    color: #333;
}

.form-section, .goal-section, .workout-list {
    margin-bottom: 20px;
}

input[type="text"], input[type="number"] {
    width: calc(100% - 22px);
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #f38a8a;
    border-radius: 4px;
}

button {
    padding: 10px 15px;
    background-color: #2047b3;
    color: rgb(241, 239, 239);
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #1143a0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    background: #eef0f1;
    margin: 5px 0;
    padding: 10px;
    border-radius: 4px;
}

script.js

  document.addEventListener('DOMContentLoaded', () => {
    const workoutForm = document.getElementById('workout-form');
    const workoutList = document.getElementById('workout-list');
    const goalInput = document.getElementById('goal');
    const setGoalButton = document.getElementById('set-goal');
    const goalDisplay = document.getElementById('goal-display');

    let workouts = [];
    let fitnessGoal = '';

    workoutForm.addEventListener('submit', (e) => {
        e.preventDefault();
        
        const exercise = document.getElementById('exercise').value;
        const duration = document.getElementById('duration').value;
        const calories = document.getElementById('calories').value;

        const workout = {
            exercise,
            duration,
            calories
        };

        workouts.push(workout);
        displayWorkouts();
        workoutForm.reset();
    });

    setGoalButton.addEventListener('click', () => {
        fitnessGoal = goalInput.value;
        goalDisplay.textContent = Your Fitness Goal: ${fitnessGoal};
        goalInput.value = '';
    });

    function displayWorkouts() {
        workoutList.innerHTML = '';
        workouts.forEach((workout, index) => {
            const li = document.createElement('li');
            li.textContent = ${workout.exercise} - Duration: ${workout.duration} minutes, Calories Burned: ${workout.calories};
            workoutList.appendChild(li);
        });
    }
});
