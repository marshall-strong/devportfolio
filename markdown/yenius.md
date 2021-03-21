# Yenius

# Resume

## Keywords

Ruby on Rails 6, PostgreSQL, JavaScript, React.js, Redux.js, SCSS, AWS, Heroku

## Description

a Kanye West-centric full-stack clone of Genius.com -- community sourced music lyrics, interpretations, and metadata

## Present Tense Bullets

- Single Page App supports a fast frontend by loading resources at launch and by only transmitting JSON data
- Bing News Search API retrieves the latest tabloid gossip on Kanye West’s impending divorce
- Redux store maintains a single source of truth on the frontend, allowing easy access to complex metadata
- BCrypt gem salts, hashes, and retrieves passwords, maintaining secure authentication from front to back
- Rails polymorphic associations prevent the need for schema changes when adding new types of metadata

## Past Tense Bullets

- Retrieved the latest tabloid gossip on Kanye West’s impending divorce with the Bing News Search API
- Managed complex metadata by using Redux to create a normalized state with a single source of truth
- Leveraged Rails polymorphic associations to avoid schema changes when adding new types of metadata
- Ensured secure user authentication by using the BCrypt gem to salt, hash, and retrieve passwords

# Technologies Used

## Frontend

### React.js

### React Hooks API

### React Router

### Redux.js

### Create React App redux template

### Bing News Search API

## Backend

### Rails 6

### PostgreSQL

### Polymorphic associations

### Counter Cache

### BCrypt gem

### Seed Generation

## Assets

### SASS

### Fonts

### SVGs

### images hosted on AWS S3

## Deployment

### Heroku local for dev enironment

### proxy unknown API requests to backend

### Heroku production deployment

- uptime-robot

## Code Style

### Prettier

### ESLint

### pre-commit

# Thoughts on Application Structure and Webpack

the file structure of this project changed multiple times over the course of development.

- manual Webpack structure
- Rails Webpacker
- 2 repositories: CreateReactApp frontend, Rails 6 API backend
- Create React App (current)

# Future Development

## CMS

add CMS access with [ActiveAdmin](https://activeadmin.info/0-installation.html#setting-up-active-admin)

## User roles

multiple user roles:

- moderators can edit, delete all Comments
- admins can add, edit ArtistCreditTypes, SampleCreditTypes
- users can add, edit Albums, Artists, Songs, Lyrics, ArtistCredits, SampleCredits

## Popups on hover

mousing over an artist link should display the artist's headshot.
the headshot should disappear when the user mouses away.
