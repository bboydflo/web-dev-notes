## npm linking and unlinking

This is inspired by the following article: https://medium.com/@alexishevia/the-magic-behind-npm-link-d94dcb3a81af

> The npm link command is special because it allows you to load a module from anywhere on your computer.
>
> <cite>Alexis Hevia<cite>

### Example

1. to link a package (example-package) globally go inside a its root folder and run

```sh
$ npm link
```

2. go inside another node project and link the `example-package`

```sh
$ npm link example-package
```

3. Now it is possible to **require** or **import** `example-package` from within this project
without installing the package.

```js
import exampleModule from 'example-package' // "example-package" is the name of the npm package
```

Now any change made to the original package `example-package` will be reflected in the current project.

> **Bonus**
> To find the path of the globally installed node modules run
> ```sh
> $ npm root -g
> ```

### Undoing npm linking

To undo the effects of `npm link` one need to remove the symbolic links.

1. go inside the package root folder un run

```sh
$ npm unlink
```

2. go inside the projects root folder and run

```sh
$ npm unlink --no-save example-package
```