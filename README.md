# Express.js Route Handler Missing Error Handling for Invalid User IDs

This repository demonstrates a common error in Express.js route handlers:  the lack of proper error handling for invalid input.  Specifically, the code attempts to parse a user ID from a route parameter but fails to handle cases where the ID is not a valid integer.

## Bug

The `bug.js` file contains the problematic code.  The route handler `/users/:id` attempts to find a user based on the provided ID. However, it doesn't check if `req.params.id` can be successfully parsed as an integer. If it can't (e.g., the ID is a string or contains non-numeric characters), the `parseInt` function will return `NaN`, causing the `find` method to fail silently or potentially throw an error.

## Solution

The `bugSolution.js` file provides a corrected version of the code.  It includes explicit error handling to check if `parseInt(userId)` results in a valid number and responds with an appropriate error message if the ID is invalid.