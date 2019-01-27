---
id: component-dependencies
title: Component Dependencies
permalink: docs/component-dependencies.html
layout: docs
category: Reference
prev: ext-testing.html
next: workspace-statuses.html
---

When a component is tagged, its dependencies are resolved, locked and written. In this section, we'll see how it affects the tagging process of components.

Traditional package managers resolve dependencies upon package installation, whereas **Bit resolves dependencies when a version of a component is being tagged**.
This makes the component dependencies immutable - the exact component version is logged.
This means Bit is able to recreate the exact same dependency tree whenever and wherever the component is installed.

## How bit automatically resolves package dependencies

There are 3 types of package dependencies for a node module; dependencies, devDependencies and peerDependencies.
Bit automates the process of defining package dependencies for a component in a project.

1. Bit reads through the code, and list all the required packages.
2. Bit parses the project's root `package.json` to get the list of project dependencies.
3. If the required package is configured in the root `package.json` of the project as a `peerDependency`, Bit will set it as a `peerDependency`.
4. If the package is required by a test-file ([read more here](/docs/add-and-isolate-components.html#tracking-a-component-with-testspec-files) about adding test files to a component), the package will be defined as a `devDependency`. Otherwise, it will be a `dependency`.
5. Bit will then generate a `package.json` file for the component.

> **Package Dependencies Edge Cases and Gotchas**
>
> * A package listed both as a `peerDependency` and a `dependency` or `devDependency` in the `package.json`,  will be considered as a peerDependency.
> * A package required by both test-file and implementation-file will be set as a `dependency`.

## Installing Component Dependencies

A sourced component's dependencies can be either installed by a package manager or sourced themselves. This section explains about the different flows and how to configure them.

This entire section is relevant only for **sourced** components. Components that are installed by a package manager function just as any other package.

## Installing a Component's Package Dependencies

A component's package dependencies are installed by a package manager, naturally.
To configure which package manager is used by Bit, head over to the [workspace's bit.json](/docs/conf-bit-json.html#packagemanager--string).

### Yarn Workspaces

Bit can install dependencies using Yarn Workspaces - this means that every component's dependencies will be installed in its own `node_modules` directory.
To use Yarn Workspaces, first configure Bit to use Yarn, and then [configure Bit to use Yarn Workspaces](/docs/conf-bit-json.html#useworkspaces--bool).

## Installing a Component's Component Dependencies

Components can depend on other components, and those can be either installed as package dependencies (node modules), or sourced as well.

Component dependencies are installed as node modules by default.
To install component dependencies as sourced components, [configure it in the workspace's bit.json](/docs/conf-bit-json.html#savedependenciesascomponents--bool).

> **Dependencies of Dependencies**
>
> When component dependencies are sourced, their own dependencies are installed as packages.


## Modify dependencies

Modifying Component Dependencies

It is possible to modify an auto-generated package.json. However, Bit does limit the possible modifications, as it will re-validate all manual modifications. Bit does it to ensure a component dependency graph is still valid. This is done whenever a component is tagged, to ensure that the component has all its dependencies defined.

Remove dependency


Bit handles the removal of dependencies automatically. Delete the require or import statement from the component’s code, and on the next tag, when the dependency graph calculation happens, Bit will remove it automatically.
Know that if you manually remove a dependency, but it is still being required in the code, Bit will add the dependency to the package.json again.

Add dependency


The only way to add a new dependency to a component’s package.json is to have it required by any of the component’s files. This means that if you add a new dependency to it by either editing the package.json or using a package manager’s --save ability, Bit will override it during the tag operation. This is to ensure that a component’s dependency graph will not end up bloated with unused dependencies.
If you want to remove dependency from a component, ensure that the code does not import or require the specific dependency, and Bit will remove it automatically.

Modify dependency version


You can manually update a dependency version in the component’s package.json file.

Modify dependency type


You can manually move a dependency from any type to any type. For example, move a dependency from dependencies to peerDependencies.