# api-pls Example

This project demonstrates how to use [api-pls](https://github.com/jmeas/api-pls)
to start up an API webserver in any project.

#### Prerequisites

- [Node.js](https://nodejs.org/en/) v7+
- a [PostgreSQL database](#how-can-i-start-a-postgresql-database-to-run-this-example)

### Getting Started

Clone this repository. Then, install the dependencies:

```sh
npm install
```

Next, create a file in the root of this project called `.env`. Add the following
line to the file, replacing the database URL with your own:

```sh
DATABASE_URL='postgres://user@example.com:5432/example'
```

Next, you'll need to create resource models. These are the definitions that
describe what tables and endpoints are created for you.

There are two examples already created for you in the `./resources` directory:
`transaction` and `category`. Review those, and make changes as you see fit.
For now, the documentation for a resource model is contained within those
example files.

Once you're satisfied with your resource models, run `npm run migrate`. This
will generate migrations from your models, and then apply them to the database.

You're now ready to start the API webserver.

Run `npm run start` to get it running. Once it's up, navigate your browser to
`localhost:5000` to begin CRUD'ing.

### FAQ

#### How can I change my resource models after the initial migration?

Eventually, api-pls will allow you to change your resources dynamically. It does
not support this now, however. If you change your resource models, you'll need
to clear all of the data in the database by running `npm run reset`.

Once that completes, you can run `npm run migrate` to bootstrap the database
with your updated models.

#### How can I start a PostgreSQL database to run this example?

To run the example, you'll need a PostgreSQL database URL. It is recommended
that you create a database specifically for testing purposes, rather than
using a database that you are using for other uses, too.

My preference is to create a free [Heroku](heroku.com) app, and then set up a
free version of
[Heroku's PostgreSQL add-on](https://elements.heroku.com/addons/heroku-postgresql).
This provides you with 10,000 rows and 20 connections for free: more than enough
than what you'll need to try out the example.

You can also set up a database locally on your machine. This will differ
slightly between operating systems. I recommend searching
[StackOverflow](stackoverflow.com) for the best solution for your OS.

#### My database does not use SSL; how can I connect to it?

You can set the "ssl" option to be `false` in your `.plsrc` file.

```json
{
  "resourcesDirectory": "./resources",
  "ssl": false
}
```
