# Yenius

[Live Site](https://yenius.herokuapp.com/)
[GitHub](https://github.com/marshall-strong/yenius)

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

# Backend

The backend is an API-only Ruby on Rails app, and uses a postgreSQL database.

## Rails 6

We are essentially using rails as an API only (I didn't create the app in API only mode, but I did delete most of the non-API stuff).

## PostgreSQL

## Routes, Controllers

## Active Record models

## Polymorphic associations

## Counter Cache

## BCrypt gem

## Seed Generation

# Frontend

The frontend is a React/Redux app, located in the `client/` direcory. It was created using [cra-template-redux](https://github.com/reduxjs/cra-template-redux), the official Redux+JS template for [Create React App](https://github.com/facebook/create-react-app).

## React.js

## React Hooks API

## React Router

## Redux.js

## Create React App redux template

_Because life is too short to configure Webpack manually_

## Bing News Search API

# Assets

## SASS

## Fonts

## SVGs

## images hosted on AWS S3

# Deployment

## Proxy API Calls

Automatically proxy API calls via the right port, without needing to swap anything between development and production.
To do this, jump into `client/package.json` and add a proxy property:

```json
"proxy": "http://localhost:3001/",
```

Once we hook everything up our scripts will be running the API on port `3001`, and we are configuring Rails to be our API.

## Heroku local for dev enironment

Having a Node server and a Rails server both running locally massviely speeds up development time. It's great for development, but overkill for production.

While we do need to run a Node server localy, we'll be depoying a pre-built bundle to heroku, and we won't need to run a Node server there.

### Heroku Command Line Interface

https://devcenter.heroku.com/articles/heroku-cli

### Procfile

[Introduction to Procfiles by Heroku](https://devcenter.heroku.com/articles/procfile)

#### Procfile.dev

```text
web: PORT=3000 yarn --cwd client start
api: PORT=3001 bundle exec rails s
```

Run the Procfile using the Heroku Command Line Interface:

```bash
heroku local -f Procfile.dev
```

Create a rake task that starts the development environment:

```ruby
namespace :start do
  task :development do
    exec 'heroku local -f Profcile.dev'
  end
end

desc 'Start development server'
task :start => 'start:development'
```

Use the rake task to start the development environment:

```bash
bin/rake start
```

One command to fire up two servers! Heroku will start the front end, /client, on port 3000, and the API on port 3001.
It’ll then open the client, http://localhost:3000 in your browser.

## Heroku production deployment

So, how do we get our Rails app serving the Webpack bundle in production?

Heroku's `heroku-postbuild` command will build the app (located in the `/client` directory), then copy the files into the `/public` directory to be served by Rails. We end up with a single Rails server manging both our front end and our back end.

### `package.json`

```json
{
  "name": "list-of-ingredients",
  "license": "MIT",
  "engines": {
    "node": "10.15.3",
    "yarn": "1.15.2"
  },
  "scripts": {
    "build": "yarn --cwd client install && yarn --cwd client build",
    "deploy": "cp -a client/build/. public/",
    "heroku-postbuild": "yarn build && yarn deploy"
  }
}
```

### [How Heroku Works](https://devcenter.heroku.com/articles/how-heroku-works)

- the `build` command uses `yarn --cwd client` to tell yarn to `cd` into the `client/` directory before running `build`
- the `post-build` command gets run after heroku has built the application, or "slug"

### uptime-robot

# Code Style

## Prettier

## ESLint

## pre-commit

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

# Acknowledgments

## [A Rock Solid, Modern Web Stack](https://blog.heroku.com/a-rock-solid-modern-web-stack)

I used this Heroku post when setting up my project.

From the post:

- [Create React App](https://github.com/facebookincubator/create-react-app)
  - All the power of a highly-tined Webpack config without the hassle.
- [Rails in API-only mode](http://edgeguides.rubyonrails.org/api_app.html)
  - Just the best bits, leaving React to handle the UI.
- [Active Admin](https://github.com/activeadmin/activeadmin)
  - An instant CMS backend.
- Seamless deployment on [Heroku](https://heroku.com/)
  - Same-origin (so no CORS complications) with build steps to manage both Node and Ruby.
- Single page app support with [React Router](https://github.com/ReactTraining/react-router)
  - So you can have lightning fast rendering on the front end.
