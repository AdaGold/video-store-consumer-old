# Project: Video Store Consumer
Create a single-page application that allows the user to interact with a library of movies. The final product will be something like the interface used at a RedBox kiosk or on Netflix.

### Learning Goals
- Explore asynchronous HTTP requests in the browser
- Leverage jQuery's event observation framework to enable dynamic interactions in the browser
- Organize browser-based javascript for reusability and maintainability
- Utilize UI/UX best practices for usability and accessibility

### Project Info
__Project API:__ For this project, use the [Video Store API](https://github.com/AdaGold/VideoStoreAPI) you created previously. Specifically, this single-page application will interact with the `/movies` endpoint(s) created for that project.

__Alternate Project API:__ I've provided a [Node/Express app to act as the project's backend API](https://github.com/AdaGold/video-store-kiosk-api). You may, __with instructor permission__, use this API instead of the API you built for the _Video Store API_ project. See the alternate API's [README](https://github.com/AdaGold/video-store-kiosk-api/blob/master/README.md) for installation and startup instructions.

__Movie Posters:__ The Alternate Project API contains a directory of [movie posters](https://github.com/AdaGold/video-store-kiosk-api/tree/master/public/images/posters). Feel free to copy this directory into your API or this single-page application if you would like to have images in your UI.

## Project Requirements
- Create this as a _Single Page Application_; no unnecessary page reloads or redirections
- Use this skeleton Node/Express application to serve a single HTML page
- That single page will provide all functionality described in these requirements 
- All movie data presented to the user must be sourced from the provided Node/Express API via AJAX

### Project Setup
- Fork and clone this repository
- After entering the project directory, install dependencies: `$ npm install`
- Start the development server: `$ npm start`

### Project Baseline
- If you are using your Video Store API, you will need to alter it to allow for cross-origin AJAX Requests via [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS).
- Add this block of code __to your API's__ `/app.js` and then restart the API server:

  ```javascript
  // enable CORS
  app.use(function(req, res, next) {
    res.header("Access-Control-Allow-Origin", "*")
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept")
    next()
  })
  ```

### Primary View
- Show a paginated collection of Movies, __10 per page__
- Allow a user to interact/select a Movie via click, touch, or some other event
  - when _selected_, a Movie shows more information
  - when _deselected_, a Movie returns to its default state
  - only __1__ movie can be selected at a time
  - selecting a second movie deselects the first
- When a Movie is selected, it can be added to the Queue
- Changing pages deselects all Movies
- Changing pages does not clear the Queue

### Queue View
- Uses a smaller section of the screen
- Shows a list of Movies the user has added to the Queue
- Exists only in the browser's memory; reloading the page will clear the Queue
- Allow a user to remove a Movie from the Queue
- Allow a user to rest/clear their Queue
- When a user pages through Movies, the Queue remains in place and does not change

### User Experience
What makes for a good kiosk user experience?

- Prioritize finger-friendliness in page design and controls
- Ensure text is clear, legible from a distance of 18 inches
- Control the structure of the page at all times; appearing elements that disrupt/change the flow of the page make for a jarring experience

### Optional Enhancements
- Sorting
  - Alter your Movies API, if necessary, to allow users to change how Movies are sorted for display
  - Add appropriate controls to this application to let a user change how Movies are sorted
- Page Size
  - Alter your Movies API, if necessary, to allow more control over how many Movies are returned per page
  - Show the appropriate number of Movies per page _based on the user's device_ (user agent)
- Queue Sorting
  - Allow a user to sort their Queue by implmenting drag-and-drop controls
