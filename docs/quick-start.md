
​
2,716 / 5,000
Translation results
Translation result
---
sidebar_position: 1
---

# Quick Start

## Overview

`fast-project` will help you with 3 main things:
- **Initiate new projects** with built-in technologies.
- **Integrate additional technologies** into a project under development in a simple way.
- **Create files based on templates**, helping to develop quickly and synchronize project structure between members.

Note: currently for project creation and technology integration, we only support projects using `nodejs`. Other platforms will be supported in the future.

## Setting

In this article I will give you some basic instructions to get acquainted with `fp`. To get started, you need to install this tool via npm:

```bash
npm install -g @fast-project/cli
```

## Create a new project

Create a directory and initialize a new project using `node generator`:

```bash
fp init node -o my-project && cd my-project
```

Use `node plugin` to create a NodeJS project structure:
```bash
fp use node
```

Use `express plugin` for express integration:
```bash
fp use express
```

With the above simple steps you have successfully created a new nodeJs project with express. Now, you can use the `yarn dev` command to run the dev server like a normal project.

> This project initialization process will create a `fast-project.json` file, which contains cli configuration information, generator and integrated plugins. If you no longer want to use `fp` in the future, you can delete this file from the project. Or, you can also use this file to initialize another project with similar configuration to the current project.

## Generate files

To quickly create an api, you can use the `fp use` command to create related files through the `express` plugin:

**Example 1**: Create api `/books`

```bash
fp use express gen -c name=book
```

**Example 2**: Create api `/book-categories`
```bash
fp use express gen -c name=book-category
```

## Edit template

Pre-built templates will certainly not be a perfect fit for your project, so in most cases you will need to edit these templates to fit your project's requirements. To do this, you can follow these steps:

**Step 1**: Extract template
You can extract and edit `express` plugin templates with the `fp extract` command:

```bash
fp extract express gen
```

**Step 2**: Edit template

These templates will be extracted in the `.templates/express/gen` folder. You can proceed to edit these files as desired. You can learn the syntax of handlebars [here](https://handlebarsjs.com/guide/).

**Step 3**: Use the new template

Use the `fp gen` command to create new files based on the edited template:

```bash
fp gen .templates/express/gen.js -c name=city
```
