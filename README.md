### Fetch
API call using async/await and fetch. The calls response Javascript Promise which must be parsed for usablility.

    const apiKey = process.env.REACT_APP_REBRANDLY_API_KEY;

    export const postUrl = async inputUrl => {
      try {
        const config = {
          method: "POST",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
            apiKey: apiKey
          },
          body: JSON.stringify({
            destination: inputUrl,
            domain: { fullName: "rebrand.ly" }
          })
        };
        const url = "https://api.rebrandly.com/v1/links";
        const rawResponse = await fetch(url, config);
        const response = await rawResponse.json();
        if (rawResponse.ok) {
          const { destination, shortUrl } = response;
          return { destination, shortUrl };
        }
      } catch (error) {
        console.log(`Something went wrong: ${error}`);
        return null;
      }
    };
##### Use the json() method of the fetch API to parse it - not JSON.parse()!

##### JSON APIs are the backbone of web services and are used to fetch, update, and manage data between a client and a server.

Basic JSON API Request Example

Using JavaScript (Fetch API):

    fetch('https://api.example.com/data')
      .then(response => response.json())  // Parse the JSON response
      .then(data => console.log(data))    // Handle the JSON data
      .catch(error => console.error('Error:', error));  // Handle errors

Example 1: Basic API Request with JSON in JavaScript

Code:

        // Fetch data from a JSON API
        fetch('https://jsonplaceholder.typicode.com/posts/1')  // Example API
          .then(response => response.json())  // Parse JSON data
          .then(data => {
            // Access and display API response data
            console.log('Post Title:', data.title);  // Output: Post Title: Example Title
            console.log('Post Body:', data.body);    // Output: Post Body: Example Body
          })
          .catch(error => console.error('API Error:', error));   
Output:

        "Post Title:"
        "sunt aut facere repellat provident occaecati excepturi optio reprehenderit"
        "Post Body:"
        "quia et suscipit
        suscipit recusandae consequuntur expedita et cum
        reprehenderit molestiae ut ut quas totam
        nostrum rerum est autem sunt rem eveniet architecto"

Explanation:

        * fetch: Sends an HTTP request to the API endpoint.
        * response.json(): Parses the response into a JSON object.
        * The parsed JSON object can be accessed like any JavaScript object.

Example 3: Sending Data to a JSON API

When converting a string to JSON, ensure it follows JSON syntax. Improper formatting can lead to errors.

JavaScript Example (POST Request):

Code:

        // Data to send to the API
        const postData = {
          title: 'New Post',
          body: 'This is the content of the post',
          userId: 1
        };
        
        // Sending a POST request to the API
        fetch('https://jsonplaceholder.typicode.com/posts', {
          method: 'POST',  // HTTP method
          headers: { 'Content-Type': 'application/json' },  // Headers
          body: JSON.stringify(postData)  // Convert data to JSON string
        })
          .then(response => response.json())  // Parse the response
          .then(data => console.log('Response:', data))  // Handle the response
          .catch(error => console.error('Error:', error));  // Handle errors
Output:

    Response: {'title': 'New Post', 'body': 'This is the content of the post', 'userId': 1, 'id': 101}


`https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch`
