# MonorepoTemplate

This is a monorepo template created using Node. Monorepos allow you to host multiple projects under a single repository. One of the challenges of setting up a monorepo is managing dependencies and shared code between projects. This template provides guidance on setting up a monorepo for a Node.js project.

## Setting up the Parent Folder

To set up the parent folder, follow these steps:

1. Create a top-level directory for your project and give it a name. For this example, we'll use "MonorepoTemplate".

2. Create a `package.json` file inside the repository by running the following code: `npm init -y`.

3. Open the `package.json` file and edit it to look like this:

```
{
  "name": "monorepo-template",
  "private": true,
  "workspaces": [
    "packages/backend",
    "packages/frontend",
    "packages/channels"
  ]
}
```

Make sure to add the `private` property and set it to `true`. Also, add the `workspaces` property and list the different projects. For file organization purposes, all the projects in this example are located in a directory called `Packages`, but you can rename this to whatever you want.

## Setting up the Projects

To set up the projects, follow these steps:

1. Open the `Packages` directory and create a directory for each project you want to include. In this example, we need to create three directories: `Frontend`, `Backend`, and `Channels`, as listed in the `workspaces` property of the main `package.json` file.

2. For each project, create a `package.json` file by running `npm init -y`.

3. Edit each `package.json` file to reference the parent `package.json`. For example, for the `Backend` project, the `name` property should be `"@monorepo-template/backend"`. Make sure to include the `version` property and set it to the correct value.

## Projects with Dependencies
Let's say we have a project that depends on another project to run effectively. For example, our **Frontend** project depends on the **Backend** project.

To ensure that the Backend project is always loaded when the Frontend project is installed or forked, you should follow these steps:

1. Add a `dependencies` property to the Frontend project's `package.json` file.
2. Add the following value to the `dependencies` property:
```
{
  "name": "@monorepo-template/frontend",
  "version": "1.0.0",

  ...

 "dependencies": {
    "@monorepo-template/backend": "1.0.0"
  }
}
```
3. Make sure you have correctly referenced the name of the Backend project's `package.json` file.
4. Ensure that you reference the correct version of the Backend project that you want to use. For example:
```
{
  "name": "@monorepo-template/frontend",
  "version": "1.0.0",
  "main": "index.js",
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "@monorepo-template/backend": "1.0.0"
  }
}

```
By following these steps, the Backend project will be installed as a dependency in the node modules and will be available for use by the Frontend project.

## Installing Dependencies for All Projects at Once

To install Node.js dependencies for all of your projects at once, navigate to the parent directory (e.g. `monorepoTemplate`) and run the following command:

```
npm install
```

This will install all of the dependencies listed in each project's `package.json` file. A `node_modules` directory will be created in the parent directory.

## Installing Dependencies for an Individual Project

To install a dependency or library for an individual project, navigate to the project folder (e.g. `Frontend`) and run the appropriate `npm` or `yarn` command. For example:

```
npm install eslint
```

This will install the dependency in the `node_modules` directory located in the project folder.








## 
If this was helpful put a star :star: on it 