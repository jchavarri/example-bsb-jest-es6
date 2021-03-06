# example-bsb-jest-es6

Example repo showing a ReasonReact project with hooks + tests, using BuckleScript `package-specs.module: "es6"` configuration.

## Run Project

```sh
yarn
yarn start
# in another tab
yarn webpack
```

After you see the webpack compilation succeed (the `yarn webpack` step), open up `build/index.html` (**no server needed!**). Then modify whichever `.re` file in `src` and refresh the page to see the changes.

## Run Project with Server

To run with the webpack development server run `yarn server` and view in the browser at http://localhost:8000. Running in this environment provides hot reloading and support for routing; just edit and save the file and the browser will automatically refresh.

Note that any hot reload on a route will fall back to the root (`/`), so `ReasonReact.Router.dangerouslyGetInitialUrl` will likely be needed alongside the `ReasonReact.Router.watchUrl` logic to handle routing correctly on hot reload refreshes or simply opening the app at a URL that is not the root.

To use a port other than 8000 set the `PORT` environment variable (`PORT=8080 yarn server`).

## Build for Production

```sh
yarn clean
yarn build
yarn webpack:production
```

This will replace the development artifact `build/Index.js` for an optimized version as well as copy `src/index.html` into `build/`. You can then deploy the contents of the `build` directory (`index.html` and `Index.js`).

If you make use of routing (via `ReasonReact.Router` or similar logic) ensure that server-side routing handles your routes or that 404's are directed back to `index.html` (which is how the dev server is set up).
