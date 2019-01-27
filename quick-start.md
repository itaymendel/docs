---
id: quick-start
title: Quick Start
permalink: docs/quick-start.html
layout: docs
category: Home
next: what-is-bit.html
---
Learn the basics of working with Bit in your own projects.

To start, choose an existing repository containing components or modules you’d like to share in other projects. We’ll learn how to use Bit to make these components available to use and even develop from other repositories.

You can also use one of our [example projects](/docs/example-projects.html), but we recommend starting with your own code.

When done, you will have a collection of the components and modules shared from the project ready to share with your team.

### Install bit

```bash
npm install bit-bin -g
```

See additional [installation methods](/docs/installation.html).

### Init Bit for your project

[Initialize a Bit workspace](/docs/initializing-bit.html) in the project’s directory.

```bash
$ cd project-directory
$ bit init
```

### Track components with Bit

Bit [isolates and tracks](/docs/add-and-isolate-components.html) files or sets of files in the repository as components, to later make them available in other projects.
To track components, use `bit add`. In this example, we’ll use a glob pattern to track all the components in the relevant directory.

```bash
bit add src/components/* # use a glob pattern or a specific path to track multiple components or a single component.
```

Bit automatically scans the files it tracks for their dependencies (packages and files), to resolve their dependency graph and isolate the components.

> **Tip**
>
> Use [bit status](/docs/cli-status.html) to verify that each component's dependency graph has been successfully built and resolved.

#### Example

Let's track the components `button`, `login` and `logo` in the following project's directory structure.

```bash
$ tree
.
├── App.js
├── App.test.js
├── favicon.ico
├── index.js
└── src
    └── components
        ├── button
        │   ├── Button.js
        │   ├── Button.spec.js
        │   └── index.js
        ├── login
        │   ├── Login.js
        │   ├── Login.spec.js
        │   └── index.js
        └── logo
            ├── Logo.js
            ├── Logo.spec.js
            └── index.js

5 directories, 13 files
```

To track these files as components we can use [bit add](/docs/cli-add.html) with a glob pattern.

```bash
$ bit add src/components/*
tracking 3 new components
```

### Add build and test tasks

To eliminate the overhead of configuring build and test environments for every component, Bit lets you choose and add build and test tasks which will apply to all the components you share.  

Read more about adding a [build environment](/docs/building-components.html) and a [test environment](/docs/testing-components.html) to your project.  

Here is a list of [pre-made build and test environments](https://bitsrc.io/bit/envs) for you to get started with quickly.  

You can [specify the component's test files](/docs/add-and-isolate-components.html#track-a-component-with-testspec-files) with `bit add` and  `--test` flag, to let Bit know these are test files and should be a part of the component.

### Tag components

[Tagging tracked components](/docs/tag-component-version.html) locks the state of the components’ files and dependency graph, and sets a semantic version to the components - thus making each component-version immutable. When you tag a component, all of its build and test tasks will run, and only if everything is working correctly, Bit will tag the components.

```bash
$ bit tag --all 1.0.0
3 components tagged | 3 added, 0 changed, 0 auto-tagged
added components:  components/button@1.0.0, components/login@1.0.0, components/logo@1.0.0
```

### Export tagged components

#### Create a Collection

Components are exported to remote Collections. Before exporting a component, first create a remote Collection - create a free account in [bitsrc.io](https://bitsrc.io/signup), and create a Collection.  

A [Collection](/docs/remote-collection.html) is similar to a git repository, that can host and manage components.  

Learn more about [organizing components in Collections](/docs/organizing-components.html) and check out [this example Collection](https://bitsrc.io/bit/movie-app) we've created for React components.

#### Authenticate Bit CLI

Authenticate Bit CLI so it can interact with Collections on [bitsrc.io](https://bitsrc.io).

Use `bit login` to open a login page in the browser. Enter your username and password and return to Bit-CLI to continue.

```bash
$ bit login
Your browser has been opened to visit: http://bitsrc.io/bit-login?redirect_uri=http://localhost:8085...
```

#### Export components

Unlike publishing packages, [exporting](/docs/cli-export.html) a component won't change the project's source code and doesn't require setting up any additional repositories.

Instead, use `bit export` to share components from your project to [bitsrc.io](https://bitsrc.io).

```bash
$ bit export user-name.collection-name  # Share components to a remote Collection
exported 3 components to collection user-name.collection-name
```

### Use components in other projects

#### Install with NPM / Yarn

All components shared with Bit can be [installed using MPM or Yarn](/docs/installing-components.html). This means every component shared on [bitsrc.io](https://bitsrc.io) can be installed and used by every developer, using Bit or not.

#### Import and develop components

To [source components](/docs/sourcing-components.html) shared with Bit into any repository and continue to develop them, use `bit import`.

The sourced and modified component can then be exported back to [bitsrc.io](https://bitsrc.io) as a new version of the component, or as a new component.

This makes it easier to maintain and modify components, and build software faster.

#### Update and sync changes

Changes to components made in different projects can be [updated](/docs/updating-sourced-components.html) and synced, and even [merged](/docs/merge-changes.html) between different repositories. This helps your team collaborate and work together.

## Summary

You now know the basics of Bit, and can start putting it to use for sharing code between your projects and with your team.

Feel free to learn more through the different sections of the docs, search [bitsrc.io](https://bitsrc.io) for components or visit [Bit on GitHub](https://github.com/teambit/bit).
