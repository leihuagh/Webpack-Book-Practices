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

```shell
npm add webpack webpack-cli -D # D === --save-dev
```

You should see webpack at your _package.json_ `devDependencies` section after this. In addition to installing the package locally below the _node_modules_ directory, npm also generates an entry for the executable.

T> You can use `--save` and `--save-dev` (`-D`) to separate application and development dependencies. The former installs and writes to _package.json_ dependencies field whereas the latter writes to `devDependencies` instead.

T> [webpack-cli](https://www.npmjs.com/package/webpack-cli) comes with additional functionality including `init` and `migrate` commands that allow you to create new webpack configuration fast and update from an older version to a newer one.

## Executing Webpack

You can display the exact path of the executables using `npm bin`. Most likely it points at _./node_modules/.bin_. Try running webpack from there through the terminal using `.\node_modules\.bin\webpack` or a similar command.

After running, you should see a version, a link to the command line interface guide and an extensive list of options. Most aren't used in this project, but it's good to know that this tool is packed with functionality if nothing else.

```shell
.\node_modules\.bin\webpack --mode development
Hash: f361806c1dbf071aa942
Version: webpack 4.32.2
Time: 152ms
Built at: 05/29/2019 11:30:24 PM
  Asset     Size  Chunks             Chunk Names
main.js  3.8 KiB    main  [emitted]  main
Entrypoint main = main.js
[./src/index.js] 28 bytes {main} [built]
```

The output tells that webpack cannot find the source to compile. It's also missing a `mode` parameter to apply development or production specific defaults.

To get a quick idea of webpack output, we should fix both:

1. Set up src/index.js so that it contains `console.log("Hello world");`.
2. Execute `.\node_modules\.bin\webpack --mode development`. Webpack will discover the source file by Node convention.
3. Examine _dist/main.js_. You should see webpack bootstrap code that begins executing the code. Below the bootstrap, you should find something familiar.

T> Try also `--mode production` and compare the output.
