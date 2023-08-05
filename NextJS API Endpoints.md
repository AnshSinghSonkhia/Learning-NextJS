# Next.js API Endpoints

Next.js allows you to create serverless API endpoints within your application using the "pages/api" directory. These API endpoints enable you to handle HTTP requests and responses directly from your Next.js server, making it convenient to integrate server-side functionality with your frontend application. Here's an overview of Next.js API endpoints, their use, and code examples:

### Creating an API Endpoint

To create an API endpoint in Next.js, you simply need to create a new file inside the "pages/api" directory. Each file in this directory represents a separate API route. The API endpoint's filename will be part of the route URL.

For example, creating a file named "hello.js" inside "pages/api" would create an API endpoint accessible at "/api/hello".

### Handling HTTP Requests

Next.js API endpoints allow you to handle different types of HTTP requests: `GET`, `POST`, `PUT`, `DELETE`, etc. The HTTP method determines how the server responds to incoming requests.

To handle different HTTP methods, you can use the `req.method` property to check the request method and implement the appropriate logic.

### Sending Responses

API endpoints need to send responses back to the client. You can use `res.status(code)` to set the HTTP status code for the response and `res.json(data)` to send JSON data as the response.

### Example: Creating a Simple API Endpoint

Here's an example of a simple API endpoint that returns a JSON response with a "message" property:

```javascript
// pages/api/hello.js

export default function handler(req, res) {
  const data = {
    message: "Hello from the API endpoint!",
  };

  res.status(200).json(data);
}
```

In this example, when you make a `GET` request to "/api/hello", the endpoint will respond with the following JSON:

```json
{
  "message": "Hello from the API endpoint!"
}
```

### Example: Handling Different HTTP Methods

You can also handle different HTTP methods in your API endpoints. Here's an example of an endpoint that handles both `GET` and `POST` requests:

```javascript
// pages/api/user.js

export default function handler(req, res) {
  if (req.method === "GET") {
    // Logic for handling GET requests
    const users = ["John", "Jane", "Tom"];
    res.status(200).json(users);
  } else if (req.method === "POST") {
    // Logic for handling POST requests
    const newUser = req.body;
    // Save the new user to the database or perform other operations
    res.status(201).json({ message: "User created successfully!" });
  } else {
    res.status(405).end(); // Method Not Allowed
  }
}
```

In this example, when you make a `GET` request to "/api/user", the endpoint will respond with an array of user names. When you make a `POST` request to the same endpoint with JSON data in the request body, the endpoint will respond with a "User created successfully!" message.

### Using API Endpoints in Frontend Components

You can call your API endpoints directly from your frontend components using standard `fetch`, `axios`, or any other HTTP library. For example, using `fetch`:

```javascript
// components/UserList.js

import { useEffect, useState } from "react";

const UserList = () => {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("/api/user")
      .then((response) => response.json())
      .then((data) => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map((user) => (
        <li key={user}>{user}</li>
      ))}
    </ul>
  );
};

export default UserList;
```

In this example, the `UserList` component fetches data from the "/api/user" endpoint and renders a list of user names on the page.

### Notes

- Next.js API endpoints are serverless and automatically deployed with your Next.js application. You don't need to set up a separate server or hosting for these endpoints.
- API endpoints should be stateless, meaning they should not rely on server-side state. If you need to manage state, consider using a separate backend server or database.
- Next.js API endpoints are ideal for handling simple backend logic, authentication, and data fetching.

With Next.js API endpoints, you have the flexibility to build both frontend and backend functionality within the same application, making it easier to develop full-stack applications with a simplified architecture.
