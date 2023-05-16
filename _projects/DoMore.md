---
title: "DoMore"
subtitle: "Efficiently manage your tasks with this simple to do list application"
date: 2023-04-26 00:00:00
description: A Todo List application built using C#, React, and ASP.NET Core to demonstrate the implementation and testing of CRUD operations in a web application.
featured_image: "/images/demo/toDoHeaderMockup.jpg"
---

![](/images/GIFMockUp/DoMoreGIF.gi)

## Table of Contents

1. [Project Description](#project-description)
2. [Technologies and Libraries](#technologies-and-libraries)
3. [Features](#features)
4. [Usage](#usage)
5. [Code Examples](#code-examples)
6. [License](#license)
7. [Contact Information](#contact-information)

## Project Description

This To-Do List Application was built to practice creating an API using C# and ASP.NET Core, as well as connecting the API to a React frontend. The goal was to practice implementing and testing all CRUD operations to better understand their use in real-world applications.

## Technologies and Libraries

The project was built using the following technologies and libraries:

- C#
- React
- ASP.NET Core
- Selenium (for testing)
- xUnit (for testing)
- MySQL (for persistent data storage)

## Features

This is a simple application that helps users keep track of tasks and mark them as complete. It allows users to:

- Create tasks with a description
- View a list of tasks
- Update existing tasks
- Delete tasks
- Mark tasks as complete
- Keep track of completed tasks
- Delete completed tasks

## Usage

Once the application is running, you can interact with it through the web interface. To create a new task, click the input and fill out the form with the task description. You can view all your tasks on the main page. To update a task, click directly on the text. To delete a task, click on the "X" to the right of the task description. To mark a task as complete, click the checkbox next to the task.

<div class="gallery" data-columns="1"">
    <img src="/images/GIFMockUp/DoMoreGif.gif">
</div>

## Code Examples

Here are some code examples demonstrating key parts of the `TaskItemsController`, which handles the CRUD operations for tasks in the project:

### Creating a Task

To create a new task, a POST request is sent to the `/tasks` endpoint with the task title and description in the request body. The `CreateTask` method in the `TaskItemsController` handles this request:

```csharp
[HttpPost]
public IActionResult CreateTask(TaskItemRequest taskItemRequest)
{
    TaskItem taskItem = new TaskItem
    {
        Title = taskItemRequest.Title,
        Description = taskItemRequest.Description
    };

    _context.Tasks.Add(taskItem);
    _context.SaveChanges();

    return CreatedAtAction(nameof(GetTaskItem), new { id = taskItem.Id }, taskItem);
}
```

### Updating a Task

To update an existing task, a PUT request is sent to the /tasks/{id} endpoint with the task ID in the URL and the updated task title, description, and completion status in the request body. The UpdateTask method in the TaskItemsController handles this request:

```csharp
[HttpPut("{id}")]
public IActionResult UpdateTask(int id, TaskItemUpdate taskItemUpdate)
{
    var taskItem = _context.Tasks.Find(id);
    if (taskItem == null)
    {
        return NotFound();
    }

    taskItem.Title = taskItemUpdate.Title;
    taskItem.Description = taskItemUpdate.Description;
    taskItem.Completed = taskItemUpdate.Completed;
    taskItem.Version++;

    _context.SaveChanges();

    return Ok(taskItem);
}
```

### Deleting a Task

To delete an existing task, a DELETE request is sent to the /tasks/{id} endpoint with the task ID in the URL. The DeleteTaskItem method in the TaskItemsController handles this request:

```csharp
[HttpDelete("{id}")]
[ProducesResponseType(StatusCodes.Status204NoContent)]
[ProducesResponseType(StatusCodes.Status404NotFound)]
public async Task<IActionResult> DeleteTaskItem(int id)
{
    var taskItem = await _context.Tasks.FindAsync(id);

    if (taskItem == null)
    {
        return NotFound();
    }

    _context.Tasks.Remove(taskItem);

    await _context.SaveChangesAsync();

    return NoContent();
}
```

## License

This project is licensed under the MIT License. For more information, please see the [LICENSE](LICENSE) file.

## Contact Information

If you have any questions, concerns, or would like to collaborate on this project, please feel free to reach out:

- Email: jonahrpena@gmail.com
- LinkedIn: [Jonah Pena](https://www.linkedin.com/in/jonahpena/)
