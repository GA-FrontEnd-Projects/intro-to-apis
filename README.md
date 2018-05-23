# Introduction to APIs
Learn the basics of APIs using the Giphy API

The term API (meaning Application Program Interface) refers to a protocol for interacting with a library or tool. For the purpose of this exercise, we're going to focus on web APIs, which are tools that popular applications make available to allow third-party developers to access the data and functionality of the application.

Most APIs these days are RESTful APIs. REST (Representational State Transfer) describes the manner in which we interact with the API, which is by passing arguments via HTTP/HTTPS (mostly in the URL, but also through request headers and through POST or PUT data for operations that change data on the server). For a full explanation of what REST entails, read [this article](https://www.sitepoint.com/developers-rest-api/).

Many APIs require consumers (users) to register for an account and pass some form of identification with each request. This can take the form of an authentication token (something that lets the server know we have an active, valid session) or an API key, or an API key and "secret", or some combination of the three. This helps make sure that users who abuse the API (sending too many requests too quickly or otherwise breaching the terms of service) can be spotted quickly by the API provider and their access can be revoked.

We will be experimenting with the [Giphy](https://giphy.com/) API today, which offers a public "beta" key that we can use for our exercise.


1) Open the [Giphy API documentation](https://developers.giphy.com/docs/) in your browser.

2) Open the index.html and script.js files in Sublime or another editor. All the HTML and CSS you'll need for this project has been written for you, but you will need to reference index.html in order to write the necessary JavaScript to complete this exercise.

3) Create an event handler for the `submit` event for the form on the page. Instead of the page reloading, display an alert box that says "Form submitted" on submit.

4) Change the alert message to "Form submitted with search term: {term}", replacing "{term}" with the text entered in the text field, saved as a variable named searchTerm.

5) Remove the alert and instead make an Ajax call to the Giphy API's "random" endpoint when the form is submitted. Refer to the Giphy documentation to find that URL. 

NOTE: Make sure you're developing in an http environment. If you opened index.html by double-clicking or by dragging the file from Sublime or another editor into your browser, you'll encounter a CORS problem at this point. You can use [Web Server For Chrome](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb?hl=en) to set up a simple server for your project.

Look at the information in the Network tab in your inspector to see what the API call returns. Note the structure of the URL -- what does each part of the URL represent?

6) The `$.ajax` method takes arguments in a number of different orders, but make sure that you're passing in an object literal as one of the arguments, and in that object, add a key called `success` whose value is an anonymous function. `success` is essentially an event handler that runs after the Ajax call comes back (also called a callback). Its first argument represents the body of the response from the server. Call this argument `data` and log its contents in the console to see what is returned.

7) If the `meta.status` value is equal to 200 (the indication that your request was successfully processed) take the `data.fixed_width_downsampled_url` argument from the returned object and create an `img` tag using that URL. Place it inside `#gif-gallery-container`.

8) Now pass the value of `searchTerm` to the API as part of the query string in the request URL in your Ajax call. Try typing "kittens" in the search box -- if the GIFs that are displayed do not contain kittens, make sure you are passing this argument to the API correctly.

9) Instead of showing a blank screen when the page first loads, let's display Giphy's top 25 trending GIFs to start. Refer to Giphy's documentation for the API endpoint you will need to use for this. You can reuse some of the code from the previous steps, but note that the response format for this endpoint is different than for the "random" endpoint.

10) Change the endpoint for our search operation to Giphy's "search" endpoint. Clear out the GIFs that we displayed from the "random" endpoint call before adding the GIFs returned by the search call. The format of the data returned from this endpoint is the same as the "trending" endpoint.

11) Explore the different configuration options for each of the endpoints in the API documentation and experiment with different values for each of the options. You can change the number of results a given call returns, which language to pull restults from, their content rating, and more.

12) If you finish the above steps early, or if you would like extra practice on your own, try creating pagination links that navigate through the pages of search results. The links should be generated based on the data in the API response rather than being hard-coded. Note that the API will only return between 25 and 100 items per call, so we will need to make additional calls to the API to get new results.