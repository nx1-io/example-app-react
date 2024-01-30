[![An old rock in the desert](https://assets-global.website-files.com/64c733db66ebf722f72bea5f/659b56a81b3593da28afb1f0_nx1-logo.svg "NX1.io")](https://nx1.io)


# Documentation for NX1 Deploy - App GitHub Workflow

## Overview
This GitHub workflow is designed for deploying an ExpressJS application using the NX1 platform. It is triggered manually and performs a series of steps to prepare, assume the necessary role, and deploy the ExpressJS application to a specified environment.

## Workflow Name

**Name**: NX1 Deploy - ExpressJS App
Run Name: This workflow will be logged as "Deploy example-expressjs-app to my environment by @<github_actor>" in the GitHub actions tab, where <github_actor> is the username of the person who triggered the run.

## Trigger

**Manual (workflow_dispatch)**: This workflow is triggered manually. It does not run automatically on any code push or pull request event. It needs to be manually dispatched from the GitHub Actions tab in the repository.

## Permissions

**id-token**: write: This workflow requires permissions to write an ID token for authentication purposes.

contents: read: It also requires read access to the repository contents.

## Jobs

### Deploy

This job runs on the latest Ubuntu runner and consists of several steps:

#### 1.**Checkout code**:

- Action: actions

Purpose: Checks out the repository code, allowing the workflow to access it.

#### 2.**NX1 Prepare Deployment**:

- Action: Prepare
- With:

    - operation: 'prepare'

    - app_id: The application ID.**Do not modify it**.

    - env_id: The environment ID where the app will be deployed.**Do not modify it**. 

    - api_token: An API token for authentication, stored in GitHub secrets. Create your api_token on [NX1.io app](https://app.nx1.io/) or read the [documentation](https://docs.nx1.io/).

Purpose: Prepares the deployment environment for the ExpressJS app using the NX1 platform.

#### 3.**NX1 Assume Role**:

- Action: `nx1-io/app-copilot-action@main`
- With:
    - operation: 'assume-role'

Purpose: Assumes the necessary role for deployment.

#### 4.**NX1 Deploy Service - expressjs-app**:

- Action: `nx1-io/app-copilot-action@main`
- With:

    - operation: 'deploy'

    - service: 'expressjs-app' (the name of the service to be deployed -**define it on NX1.io app**)

Purpose: Deploys the ExpressJS application to the specified environment.

### Additional Notes

**Version**: This document corresponds to the first revision of the workflow (rev:1).

**Security**: The workflow uses a secret (NX1_API_TOKEN) for the API token, ensuring security and confidentiality.

**Customization**: To adapt this workflow for different applications or environments, modify the api_token.



# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
