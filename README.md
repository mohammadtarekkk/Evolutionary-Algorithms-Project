# University Timetable Scheduling System with PSO

An intelligent university timetable scheduling system that uses **Particle Swarm Optimization (PSO)** algorithm to automatically generate optimal course schedules. The system features a user-friendly GUI built with Tkinter and handles complex scheduling constraints for courses, doctors, halls, and departments.

## 🚀 Features

- **Particle Swarm Optimization**: Advanced metaheuristic algorithm for optimal schedule generation
- **Interactive GUI**: User-friendly interface for parameter input and timetable visualization
- **Constraint Handling**: Manages complex scheduling constraints including:
  - Doctor availability conflicts
  - Department course conflicts
  - Hall capacity restrictions
  - Daily lecture limits
- **Multi-Day Scheduling**: Generates schedules for 5 working days (Sunday-Thursday)
- **Real-time Visualization**: Dynamic timetable display with course and instructor information
- **Flexible Configuration**: Customizable PSO parameters for fine-tuning

## 📋 Requirements

```
tkinter
numpy
scikit-learn
matplotlib
json
```

## 🛠️ Installation

1. Clone this repository:
```bash
git clone https://github.com/mohammadtarekkk/Evolutionary-Algorithms-Project.git
cd timetable-scheduling-pso
```

2. Install required packages:
```bash
pip install numpy scikit-learn matplotlib
```

3. Ensure you have the required JSON data files in the project directory:
   - `courses.json`
   - `doctors.json`
   - `halls.json`
   - `departments.json`

## 📊 Data Structure

### Required JSON Files

#### `courses.json`
```json
{
  "courses": [
    {
      "code": "CS101",
      "name": "Introduction to Computer Science",
      "doctor": "Dr. Smith"
    }
  ]
}
```

#### `doctors.json`
```json
{
  "doctors": [
    {
      "name": "Dr. Smith",
      "courses": ["CS101", "CS102"]
    }
  ]
}
```

#### `halls.json`
```json
{
  "halls": [
    {
      "name": "Hall A",
      "capacity": 500
    },
    {
      "name": "Hall B", 
      "capacity": 200
    }
  ]
}
```

#### `departments.json`
```json
[
  {
    "Level 1": [
      {
        "name": "Computer Science",
        "courses": [
          {"course": "CS101"},
          {"course": "CS102"}
        ]
      }
    ]
  }
]
```

## 🔧 Usage

### Running the Application

1. **Execute the notebook or convert to Python script**:
```bash
python timetable_scheduling.py
```

2. **Configure PSO Parameters**: 
   - A dialog will appear asking for PSO parameters:
     - **Swarm Size**: Number of particles in the swarm (recommended: 20-50)
     - **Max Iterations**: Maximum number of iterations (recommended: 100-500)
     - **w (Inertia Weight)**: Controls particle momentum (recommended: 0.5-0.9)
     - **c1 (Cognitive Parameter)**: Personal best influence (recommended: 1.5-2.0)
     - **c2 (Social Parameter)**: Global best influence (recommended: 1.5-2.0)

3. **View Generated Timetables**: 
   - The system will generate and display timetables for each day of the week
   - Each window shows a day's schedule with halls and time slots

### Example PSO Parameters

For optimal results, try these parameter combinations:

| Parameter | Conservative | Balanced | Aggressive |
|-----------|-------------|----------|------------|
| Swarm Size | 20 | 30 | 50 |
| Max Iterations | 100 | 200 | 500 |
| w | 0.7 | 0.6 | 0.5 |
| c1 | 1.5 | 1.8 | 2.0 |
| c2 | 1.5 | 1.8 | 2.0 |

## 🏗️ System Architecture

### Core Components

1. **Data Loading & Encoding**:
   - JSON file parsing
   - Label encoding for courses and doctors
   - Department-course mapping

2. **Constraint Management**:
   - Doctor conflict detection
   - Department overlap prevention
   - Hall capacity validation
   - Daily lecture limits

3. **PSO Algorithm**:
   - Particle initialization with random valid positions
   - Fitness evaluation based on constraint violations
   - Velocity and position updates
   - Global and local best tracking

4. **GUI Components**:
   - Parameter input dialogs
   - Timetable visualization grids
   - Multi-window day views

### Schedule Structure

- **Time Slots**: 4 slots per day (8-10, 10-12, 12-2, 2-4)
- **Halls**: 7 halls with different capacities
- **Days**: 5 working days (Sunday-Thursday)
- **Constraints**: No conflicts, optimal resource utilization

## 📈 Algorithm Details

### Particle Swarm Optimization

The PSO algorithm optimizes the timetable by:

1. **Initialization**: Creates random valid schedules
2. **Fitness Evaluation**: Calculates constraint violations:
   ```python
   fitness = doctor_conflicts + department_conflicts + lecture_limit_violations
   ```
3. **Position Updates**: Uses velocity equations:
   ```python
   velocity = w * velocity + c1 * r1 * (personal_best - position) + c2 * r2 * (global_best - position)
   ```
4. **Constraint Handling**: Ensures schedule validity through smart initialization

### Optimization Objectives

- **Minimize Doctor Conflicts**: No doctor teaches multiple courses simultaneously
- **Minimize Department Conflicts**: No department has overlapping courses
- **Respect Hall Capacities**: Large courses in large halls, small courses in small halls
- **Limit Daily Lectures**: Maximum 4 lectures per day

## 🎨 GUI Features

### Parameter Input Dialog
- Clean input form for PSO parameters
- Validation and error handling
- User-friendly parameter descriptions

### Timetable Display
- **Color-coded cells**: Alternating colors for better readability
- **Course Information**: Shows course code and instructor name
- **Multi-day Windows**: Separate window for each day
- **Responsive Layout**: Adjusts to content size

## 🔍 Troubleshooting

### Common Issues

1. **JSON File Errors**: Ensure all JSON files are properly formatted and in the correct directory
2. **Parameter Values**: Use reasonable PSO parameter ranges as suggested above
3. **Memory Issues**: Reduce swarm size or iterations for large datasets
4. **GUI Issues**: Ensure tkinter is properly installed on your system

### Performance Optimization

- **Reduce Swarm Size**: For faster execution with smaller datasets
- **Increase Iterations**: For better quality solutions with complex constraints
- **Adjust Inertia Weight**: Lower values for faster convergence, higher for exploration

## 🤝 Contributing

Contributions are welcome! Areas for improvement:

- **Additional Constraints**: Room preferences, time preferences
- **Algorithm Enhancements**: Hybrid algorithms, adaptive parameters
- **GUI Improvements**: Better visualization, export functionality
- **Performance Optimization**: Parallel processing, caching

## 🙏 Acknowledgments

- Particle Swarm Optimization algorithm by Kennedy and Eberhart
- Tkinter GUI framework
- scikit-learn for data preprocessing utilities

---

**Note**: This system is designed for academic scheduling and can be adapted for various educational institutions with different constraints and requirements.
