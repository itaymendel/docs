---
id: what-is-bit
title: What is Bit?
permalink: docs/what-is-bit.html
redirect_from:
  - "docs/faq-what-is-bit.html"
layout: docs
category: Home
prev: quick-start.html
next: example-projects.html
---

Here you will learn what is bit and how to best utilize it for your needs.

[Bit](https://bitsrc.io) is a component-as-a-service platform that helps software developers to organize the components of their codebase, make them discoverable, sync them between different projects and use them to build new features and products faster. With Bit, you can focus on product and technological innovation instead of having to reinvent the wheel.

Bit is a collaborative open source project, actively developed and maintained by a venture-backed team and used by more teams and communities every day.

## Advantages of using Bit

Every day more of the software we build is designed with encapsulated, reusable components. From UI and Web components to Node.js modules, utility functions, GraphQL APIs and even serverless functions, these components are our building blocks.

The JS community has done significant progress towards component-driven architectures. From the [Node.js module system](https://nodejs.org/api/modules.html) to native [Web Components](https://developer.mozilla.org/en-US/docs/Web/Web_Components) and  great frameworks like [React](https://reactjs.com), [Angular](https://angular.io) and [Vue](https://vuejs.org/). Guidelines for building components were wonderfully described by Addy Osmani in his post about the [FIRST principle](https://addyosmani.com/first/).

Bit organizes your components and makes them discoverable to use and develop from different projects while keeping them synced across your codebase.

#### Discoverability and access to all your components 

Bit hosts and organizes your components to make them [visible](https://blog.bitsrc.io/introducing-the-live-react-component-playground-d8c281352ee7) and discoverable for you and your team to collaborate on. Leveraging existing components and evolving them over time lets you focus on building new features and products without having to reinvent the wheel every day.

#### Reducing publish and maintenance overhead

Bit works with Git and NPM to eliminate the overhead around shared code. Instead of splitting and refactoring repositories while making changes across multiple projects, Bit lets you [seamlessly isolate](https://blog.bitsrc.io/how-to-publish-multiple-packages-from-any-repository-in-5-minutes-9aafd31d85b7) components in existing repositories and use them in other projects. With Bit, you can **increase** code sharing while **reducing** the overhead around it.

#### Collaboration across projects

Components shared with Bit can be developed and evolved from any project in your codebase, while changes can be easily [updated and merged](https://medium.com/p/b943656e75e3/edit) between your projects. This helps you avoid duplicate code, manage shared components at scale and increase the maintainability of your entire codebase through better collaboration across projects and teams.

## What is a Bit component?

A Bit component is a set of tracked files in a project. For each component Bit calculates a dependency graph and creates an isolated component environment.

## What is a good candidate to be a Bit component?

A code component is an encapsulated piece of code which should handle a single responsibility, representing a well-defined functionality and composable with other components to build larger things. These components can be files or sets of files handled by Bit.

You can learn more in this [post](https://addyosmani.com/first/) by Addy Osmani.

## What are common use cases for Bit?

Popular use cases for Bit are syncing [UI components](https://blog.bitsrc.io/how-to-easily-share-react-components-between-projects-3dd42149c09) between apps, sharing common [Node.js code](https://blog.bitsrc.io/how-we-successfully-share-and-reuse-code-between-microservices-at-scale-20fcfaebc6d0) between microservices, working with [GraphQL APIs](https://blog.bitsrc.io/make-your-graphql-api-easier-to-adopt-through-components-d84810e75eea), turning [shared libraries](https://blog.bitsrc.io/turning-your-component-library-into-a-component-playlist-with-bit-a8cae43f0f9d) into component “playlists” and even syncing utility functions. You can also use Bit to more easily [open-source parts](https://blog.bitsrc.io/how-to-open-source-parts-of-your-private-project-with-bit-113cc2e1af9c) of existing private projects.

Bit is also valuable for the following project structures:

- **Multi-Repo** - When using a multi-repo or a microservices architecture, Bit is useful for sharing and syncing code between projects and services with 2-way development and change syncing.

- **Single Repository with Multi-Package Publishing** - When using this kind of repository, also known as a “monorepo”, Bit is useful for organizing its components and making them discoverable, syncing them in other projects etc.

- **Shared Libraries** - Bit can make all the components within these libraries available to discover, test, monitor, use and develop from any other project.

Bit can also be used to turn any existing repository into a virtual multi-package repository, without having to refactor or restructure it. Instead, you can make different parts of its existing structure available for installation with NPM and Yarn or to be consume with Bit from other repositories.
