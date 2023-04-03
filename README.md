# BoreSquare App

BoreSquare is a web application similar to FourSquare that aggregates location data. It allows users to view a list of locations, like or remove like on a location, and create their own locations. The app uses Redis, React, and GraphQL as its primary technologies.

## Features

- The application allows users to view a list of locations obtained through the Places API
- Users can like or remove likes from a location, and the app will save the location in Redis accordingly.
- Users can view their liked locations and previously created locations.
- Users can delete their previously created locations.
- Users can create new locations by filling out the form available at '/new-location'

## Technologies

- React: a popular JavaScript library for building user interfaces
- GraphQL: an API query language and runtime for building APIs
- Apollo Client: a fully-featured GraphQL client
- Apollo Server: an open-source GraphQL server that supports real-time data
- Redis: an in-memory data structure store used for caching purposes
- Places API: an API provided by FourSquare that allows users to search for locations based on various parameters.

## Getting Started

To get started with BoreSquare, clone the repository and follow the instructions below:

- Run npm install to install all necessary dependencies.
- Run npm run dev to start the development server.
- Open http://localhost:3000 in your browser to view the application.

## Backend

The backend of the application is implemented using Apollo Server, and it supports the following queries and mutations:

### Queries

- 'locationPosts(pageNum: Int)': retrieves a list of locations obtained through the Places API.
- 'visitedLocations': retrieves a list of the user's liked locations.
- 'userPostedLocations': retrieves a list of the user's previously created locations.'

### Mutations

- 'uploadLocation(image: String!, address: String, name: String)': creates a new location and saves it in Redis.
- 'updateLocation(id: ID!, image: String, name: String, address: String, userPosted: Boolean, visited: Boolean)': updates an existing location.
- 'deleteLocation(id: ID!)': deletes an existing location.

## Frontend

The frontend of the application is built using React and Apollo Client. The application consists of the following pages:

- '/': displays a list of location results from the Places API. A user can click a "Get More" button to perform another query to get more locations.
- '/my-likes': displays a list of locations that the user has previously liked.
- '/my-locations': displays a list of locations that the user has previously created. The user can delete their locations from this page and can only upload new locations from here as well.
- '/new-location': renders a form that allows users to create new locations.

## Special Behavior

- If a user adds a location obtained through the Places API to their liked locations, the application saves the location in Redis. However, if the location is user-posted, it will remain in Redis even if the user doesn't add the post to their likes.
- Any failures, such as the failure to like an image or to delete a location, will fail gracefully by displaying a message.

## Credits

This application is built as a part of the CS-554 course at Stevens Institute of Technology.
