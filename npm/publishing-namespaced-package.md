# Publish Namespaced Packages

Sometimes you want to publish a package under a specific scope, so that it is clear that the package is related to a certain organization, or group of related packages or maybe you just want to name your package `@myname/mypackage` instead of `mypackage` or it conflicts with another package name. Here is how you can do that.

1.  **Create a new package**

    First, create a new package or use an existing package. If you are creating a new package, you can use `npm init --scope=@yourname` to create a new package.

    ```sh
    npm init --scope=@yourname
    ```

    This will create a new package with the scope `@yourname`. Make sure to replace `@yourname` with your actual scope. The scope should be your npm username or your organization name.

    If you are using an existing package, you can add the scope to the `name` field in the `package.json` file.

    ```json
    {
      "name": "@yourname/mypackage",
      "version": "1.0.0",
      "description": "My package",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "keywords": [],
      "author": "",
      "license": "ISC"
    }
    ```

2.  **Publish the package**

    After you have created the package, you can publish it to npm using the `npm publish` command.

    ```sh
    npm publish
    ```

    This will publish the package to npm with the scope you have specified. By default, it will publish the package in private mode and you need to pay for a private package. If you want to publish it as a public package, you can use the `--access` flag followed by `public` on your first publish.

    ```sh
    npm publish --access public
    ```

    This will publish the package as a public package.

    Another way to make sure the package published as a public package is to add the `publishConfig` field in the `package.json` file.

    ```json
    {
      "name": "@yourname/mypackage",
      "version": "1.0.0",
      "description": "My package",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "keywords": [],
      "author": "",
      "license": "ISC",
      "publishConfig": {
        "access": "public"
      }
    }
    ```

    And then run `npm publish` without the `--access` flag to publish the package.

3.  **Install the package**

    After you have published the package, you can install it using the `npm install` command.

    ```sh
    npm install @yourname/mypackage
    ```

    This will install the package with the specified scope.

That's it! You have successfully published a package with a specific scope to npm.

### Reference

- [Getting Error 402 while publishing package using npm | StackOverflow](https://stackoverflow.com/questions/41981686/getting-error-402-while-publishing-package-using-npm)
