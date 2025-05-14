Fetch
I rewrote the API call using async/await and fetch. The response of the fetch call is a Javascript Promise. You have to parse it to make it useful.

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
But you have to use the json() method of the fetch API to parse it - not JSON.parse()!
