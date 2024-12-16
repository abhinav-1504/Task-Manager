# Task Manager Application

This is a robust console-based **Task Manager Application** implemented in C++ using the Singleton design pattern, forward lists for task storage, and file handling for data persistence. The application offers an intuitive interface to manage tasks, including adding, deleting, and viewing tasks, with automatic storage and retrieval from a file.

## Features

1. **Add Task**:
   - Allows the user to add a new task.
   - Each task includes a title, description, and due date.
   - The task is saved in an internal forward list and persisted in a file (`mytasks.txt`).

2. **Delete Task**:
   - Deletes a task based on the provided task title.
   - Updates the internal list and the storage file accordingly.
   - Provides feedback if the task title is not found.

3. **View All Tasks**:
   - Displays all stored tasks in a clear and organized format.
   - Shows the task's title, description, and due date.

4. **Data Persistence**:
   - Tasks are saved in a file (`mytasks.txt`) to ensure they persist across program runs.
   - Tasks are automatically loaded when the program starts.

5. **Singleton Design Pattern**:
   - Ensures that only one instance of the Task Manager exists at a time.

## File Structure

- **`mytasks.txt`**: A text file used to store task details. Each task is stored in the following order:
  - Title
  - Description
  - Due Date

## How to Run

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/Task_Manager.git
    cd Task_Manager
    ```

2. Compile the program using a C++ compiler:
    ```bash
    g++ -o Task_Manager main.cpp
    ```

3. Run the program:
    ```bash
    ./Task_Manager
    ```

## Usage Guide

### Menu Options

Upon running the application, the following menu options will be displayed:

1. **Add New Task**:
   - Enter a unique task title.
   - Provide a description and a due date.
   - Task is successfully added and saved.

2. **Delete Task**:
   - Enter the title of the task you wish to delete.
   - If the title matches an existing task, it will be removed.
   - If no match is found, a message is displayed.

3. **View All Tasks**:
   - Displays all tasks stored in the task manager.
   - Each task is shown with its title, description, and due date.

4. **Exit**:
   - Saves all tasks to the file.
   - Exits the program.

### Example Workflow

- **Start** the application.
- **Add tasks** with details like title, description, and due date.
- **View the task list** to confirm the addition.
- **Delete a task** by entering its title.
- **Exit** to save and close the application.

## Implementation Details

### Singleton Design Pattern

- **Purpose**: Restricts the instantiation of the `TaskManager` class to a single instance.
- **Implementation**: 
  - Uses a static boolean variable (`isObjectCreated`) to track whether an instance exists.
  - Provides a `getTaskManager()` static method to return the single instance.

### Task Management with `forward_list`

- **Why `forward_list`**: Provides lightweight, singly linked list functionality, ideal for simple task management.
- **Operations**:
  - Adding tasks: Uses `push_front` for efficiency.
  - Deleting tasks: Uses iterators to locate and remove specific tasks.
  - Traversing tasks: Iterates through the list to display task details.

### File Handling

- **Loading Tasks**:
  - Reads tasks from `mytasks.txt` into the forward list when the program starts.

- **Saving Tasks**:
  - Writes tasks from the forward list to `mytasks.txt` when the program exits.

- **Error Handling**:
  - If the file does not exist, a new one is created during task addition.

### TaskNode Class

- Represents a single task with:
  - Title
  - Description
  - Due Date
- Provides getter methods for each attribute.
- Includes a `printTask()` method to neatly display task details.

### TaskManager Class

- Manages the task lifecycle (add, delete, view).
- Handles file operations for data persistence.
- Ensures singleton behavior.

## Example Task File Format

Below is an example of how tasks are stored in `mytasks.txt`:

```
Task Title 1
Description of Task 1
2024-12-31
Task Title 2
Description of Task 2
2024-12-25
```

## Limitations

- Task titles must be unique; the program does not enforce this but relies on user input.
- Date validation is not implemented; the user must ensure correct formats.
- Console-based application without a GUI.

## Future Enhancements

1. Implement proper date validation and formatting.
2. Add task priorities (e.g., High, Medium, Low).
3. Enhance the user interface with a graphical or web-based design.
4. Integrate database support for more robust task management.

## Dependencies

- C++ Standard Libraries: `<iostream>`, `<fstream>`, `<forward_list>`, `<string>`, `<cstdlib>`, `<cstdio>`.
