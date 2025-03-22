# sit737-2025-prac2p

A simple Node.js Express application that allows users to submit their name via a form and receive a personalized greeting.

## Project Setup

### Prerequisites

- Node.js and npm installed on your system
- Git installed on your system

### Installation Steps

1. Create a new GitHub repository named `sit737-2025-prac2p`

2. Clone the repository to your local machine:
   ```
   git clone https://github.com/your-username/sit737-2025-prac2p.git
   cd sit737-2025-prac2p
   ```

3. Initialize the Node.js project:
   ```
   npm init -y
   ```

4. Install Express:
   ```
   npm install express
   ```

5. Create an `index.js` file with the following code:
   ```javascript
   // Step 1: Load the Express framework
   const express = require('express');
   // Step 2: Create an instance of an Express app
   const app = express();
   // Step 3: Specify the port number for the server
   const PORT = 3000;
   // Step 4: Enable parsing of form data submitted via POST requests
   // This makes it possible to retrieve form inputs through req.body
   app.use(express.urlencoded({ extended: true }));
   // Step 5: Route to display the name input form on the homepage
   app.get('/', (req, res) => {
     // Return a simple HTML form where the user can enter their name
     res.send(`
       <h2>Enter Your Name</h2>
       <form action="/submit" method="POST">
         <input type="text" name="name" placeholder="name" required/>
         <button type="submit">Submit</button>
       </form>
     `);
   });
   // Step 6: Route to handle the form data after submission
   app.post('/submit', (req, res) => {
     // Get the name value from the submitted form
     const name = req.body.name;
     // Respond with a greeting and a link to return to the form
     res.send(`<h2>Hello, ${name}!</h2> <a href="/">Go Back</a>`);
   });
   // Step 7: Launch the server and listen for incoming requests
   app.listen(PORT, () => {
     console.log(`Server is running on http://localhost:${PORT}`);
   });
   ```

## Running the Application

Start the application with:
```
node index.js
```

Then open your browser and navigate to `http://localhost:3000`

## Application Overview

This simple Express application:

1. Creates a server that listens on port 3000
2. Displays a form on the homepage where users can enter their name
3. Processes form submissions via POST request
4. Returns a personalized greeting with the submitted name
5. Provides a link to go back to the form

## Code Explanation

- **Express Setup**: Initializes the Express application and configures middleware
- **GET Route**: Handles requests to the root path by serving an HTML form
- **POST Route**: Processes form submissions, extracts the name, and returns a greeting
- **Server Initialization**: Starts the server on the specified port
