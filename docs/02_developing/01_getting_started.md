# Getting Started

Before getting started, make sure you are using a recent version of [Node](https://nodejs.org/en/). You should use at least the most current LTS (long-term support) version. The configuration of the book has been written with the LTS Node features in mind. You should have `node` and `npm` commands available at your terminal. [Yarn](https://yarnpkg.com/en/) is a good alternative to npm and works for the tutorial as well.

It's possible to get a more controlled environment by using a solution such as [Docker](https://www.docker.com/), [Vagrant](https://www.vagrantup.com/) or [nvm](https://github.com/nvm-sh/nvm). Vagrant comes with a performance penalty as it relies on a virtual machine. Vagrant is valuable in a team: each developer can have the same environment that is usually close to production.

T> The completed configuration is available at GitHub.

## Setting Up the Project

To get a starting point, you should create a directory for the project and set up a _package.json_ there. npm uses that to manage project dependencies. Here are the basic commands:

```shell
mkdir codes
cd codes
npm init -y # -y generates *package.json*, skip for more control
```

You can tweak the generated package.json manually to make further changes to it even though a part of the operations modify the file automatically for you. The official documentation explains [package.json options](https://docs.npmjs.com/files/package.json) in more detail.

T> You can set those `npm init` defaults at _~/.npmrc_.

T> This is an excellent chance to set up version control using [Git](https://git-scm.com/). You can create a commit per step and tag per chapter, so it's easier to move back and forth if you want.

T> The book examples have been formatted using [Prettier](https://www.npmjs.com/package/prettier) with <code>"trailingComma": "es5"</code>, and <code>"printWidth": 68</code> options enabled to make the diffs clean and fit the page.

## Installing Webpack

Even though webpack can be installed globally (<code>npm add webpack -g</code>), it's a good idea to maintain it as a dependency of your project to avoid issues, as then you have control over the exact version you are running. The approach works nicely in **Continuous Integration** (CI) setups as well. A CI system can install your local dependencies, compile your project using them, and then push the result to a server.

To add webpack to the project, execute:
