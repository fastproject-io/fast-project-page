---
sidebar_position: 1
---

# Quick Start

Let's discover **fp** command in less than 5 minutes.

## Getting Started

### What you'll need

- [Node.js](https://nodejs.org/en/download/) version 12.0 or above

- **fp** cli tool, available via install from npm 
```bash
npm install -g @fast-project/cli
```

### Prepare your project

To save time, we recommend that you clone our examples repository to your local machine:

```bash
git clone git@github.com:fast-project/fast-project-examples.git
```

In this guide, we will use `node-express-app` example.

```bash
cd fast-project-examples/node-express-app
```

### Start generating files

The `.templates` dir in the root of the `node-express-app` example is the template directory. It contains all the templates that will be used to generate files. 
To start generating files, run the following command:

```bash
fp gen --template .templates --config route=book --config view=book
```

Command above will generate 2 new files: `src/routes/book.js`, `src/views/book.js` and add the `book` route to the existing `src/app.js`.

Run the following command to start the app:

```bash
npm start
```

Then, open your browser and navigate to `http://localhost:3000/books` to see the result.

You can repeat the command `fp gen` with different `route` and `view` values to generate more files.
