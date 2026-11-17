# expense-tracker
A student keeps a text file of expenses, one per line, in the form category,amount. Write a Node.js script that loads this file and reports on it.


# README

### 1. What did you predict for Warmup.js, and what did it print? Explain the first line and the error from Part B.

I predicted that the first line would print `undefined` because JavaScript hoists the `var` declaration but does not assign its value until that line executes. It printed `undefined`, followed by `99 1` and `3`. In Part B, uncommenting `console.log(b)` caused a `ReferenceError` because `let` variables cannot be accessed before their declaration due to the Temporal Dead Zone.

### 2. Why did Loop finished print before Async read finished? Who did the reading while your loop was running?

`fs.readFile()` is asynchronous, so Node.js starts the file-reading operation and continues executing the remaining code without waiting for it to finish. The event loop allows the program to continue, while the operating system handles the file I/O in the background. Once the reading is complete, the callback runs and prints `Async read finished`.

### 3. How does tracker remember spent after createBudgetTracker has returned?

The tracker remembers `spent` because of a concept called a closure. The returned inner function keeps access to the `spent` variable from its outer function, even after `createBudgetTracker()` has finished executing. This allows the tracker to update and remember the total amount spent every time it is called.

### 4. What does the ^ in front of the lodash version in package.json mean, and why is package-lock.json created?

The `^` symbol means npm can install compatible newer minor and patch versions of lodash, while keeping the same major version. The `package-lock.json` file is created to record the exact dependency versions installed, so the project can be installed consistently on different systems. Shareesh