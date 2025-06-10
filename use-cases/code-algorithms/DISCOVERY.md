Exercise Part 1: Understanding Project Structure<br />
Imagine you’ve just been asked to work on the Task Manager project but have no prior knowledge of its structure or technologies.

Write down your best guess about how the codebase is organized<br />
The files are located in the main directory. There is a separate directory for the tests.


List the technologies and frameworks you think it uses<br />
I think this project uses Node and Node Package manager.

Identify what you think are the main components<br />
I think app.js is the main component, and cli.js is the command-line part of the tool. 

Record any misconceptions you had<br />
I didn’t recognise that there was a framework being used for testing - Jest. I didn’t see the framework being used for the CLI functions either - Commander. 


Note important entry points and architectural patterns identified<br />
cli.js is the command-line interface for the program.


List the key components and their responsibilities<br />
cli.js is the command-line interface for the program.
app.js is the main file
storage.js keeps memory of the task
Package.json loads the frameworks from NPM


Exercise Part 2: Finding Feature Implementation<br />
Imagine your team lead has asked you to add a new feature: "Task Export to CSV". You need to first understand how similar features are implemented.

Search for any existing export or file-related functionality in the codebase<br />
Storage.js keeps all of the records. This is where I would put an export feature.

Based on your initial search, write down where you think task data export functionality might belong<br />
I think Storage.js is where task data export functionality may be. 

Note which existing components might need to be modified<br />
getAllTasks() and save() may need to be modified to add write to file functionality. 


List search terms you used and files you found<br />
I searched the code with terms like “export” and “file”. This led me to storage.js. 


Map out where in the codebase you would implement this new feature<br />
I would use the save() function in storage.js, as this contains writeFileSync which allows a file to be written to a specific location.


Exercise Part 3: Understanding Domain Model<br />
Identify the core entity classes (Task, TaskStatus, TaskPriority, etc.)
TaskManager, Task, TaskStorage

Look for business logic related to tasks<br />
The task object is created in models.js. It has a title, description, unique ID, status and more features. The task can be marked as done and as overdue. The task has different priorities and statuses.

Exercise Part 4: Practical Application<br />
Your team needs to implement a new business rule: "Tasks that are overdue for more than 7 days should be automatically marked as abandoned unless they are marked as high priority."

Identify which files you would need to modify<br />
app.js would need to be modified. It already has functionality to determine if a task has been created over 7 days ago.

Outline the changes you would make to implement this rule<br />
We would need to create a new function that utilises app.js’s getStatistics() function to determine which tasks are overdue. 

We would need to add a new key/value pair to the models.js Task constructor, called abandoned. If the task was returned as overdue by the getStatistics() function, we would need to update the task’s abandoned value to be equal to true. 


