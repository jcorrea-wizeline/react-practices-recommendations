# React JS structure

## How to structure a react app

There is not a silver bullet answer to this question, always is going to depend on the project requeriments. The next explanation is a recommendation considering different aspects of a project.

There are different ways to create and structure a React app, it depends mostly on:

- Scope and size of the project.
- The number of features.
- If SSR is necessary or not.

Also, we have different architecture styles:

- SPA.
- Micro frontend.

And that is going to influence the CI/CD.

## Recommended structure for a small app

If the app is going to be like 3 views, we can consider it as "small". One possible structure for this is structure by file type.

```
src/
..../components
..../views
..../hocs
..../hooks
..../interfaces
..../services
..../etc
```

Where each folder will holds the corresponding file type, like `components/button.tsx`.

## Recommended structure for a medium or big app

If the app is going to be with multiple views, or it will handle authentication and authorization mechanism, one way to structure the app is structure by feature.

```
src/
..Auth/
..../components
..../views
..../hocs
..../hooks
..../interfaces
..../services
..../etc
..ModuleA/
..../components
..../views
..../hocs
..../hooks
..../interfaces
..../services
..../etc
..ModuleX/
..../components
..../views
..../hocs
..../hooks
..../interfaces
..../services
..../etc
```

Where internally, each feature can contains a structure by file type. This makes predectible on make changes and if we do each feature as independent as possible, we will have the flexibility to sepparate them if necessary.

## Recommendation about the tests ubication

Is recommended to define the test files alongside the file that they are testing, so as developer, we can find quickly where is the test and the navigation is simplified.

```
..Auth/
..../components
....../button
........button.jsx
........button.test.jsx
```

## React ecosystem dependencies

React JS ecosystem dependencies recommended for a project that needs to be done quickcly.

- [react-router-dom](https://www.npmjs.com/package/react-router-dom). If there are more than one page, for navigate between pages, good fit for SPA.
- [react-query](https://react-query-v3.tanstack.com/). If there are API Rest (or just webservice endpoints), it's a great way to handle those requests, including cache feature from FE side if necessary.
- [mui](https://mui.com/). Is one of the most used and popular UI library that provides theme customization, styled-components and different tools for create UI quickly.
- [react-hook-form](https://react-hook-form.com/). Is a great way to handle the forms logic with customizations ways and has a good performance since the forms are not re rendering on change (use of useRef internally).
- [yup](https://www.npmjs.com/package/yup). As complement of react-hook-form, it helps for form validations.
- [react-testing-library](https://testing-library.com/docs/react-testing-library/intro/). For unit and integrations tests, is one of the most popular testing tools, the api is friendly with the good testing practices in FE.
- [jest](https://jestjs.io/). As test runner, mock/stub and assert validations.
- [mock-service-worker](https://mswjs.io/). For best practices about testing FE app with api calls.
- [cypress](https://www.cypress.io/). Known for E2E tests, we can also use it optionally for integration tests, it's recommended when the tests are slow using jest and react testing library (like test a navigation from view A to view B).

Note: TypeScript is recommended for a better development quality and experience.
