# How to generate an react application

## Local requirements:

- npm
- node.js

Run below command:
npx create-react-app <Name of the project>

Documentation:
https://create-react-app.dev/docs/getting-started#npx

Inside projects root folder:

- Starts the development server.
  yarn start

- Bundles all the js files into static files for production.
  yarn build

- Starts the test runner.
  yarn test

# Development using docker cli

## Using a custom named Dockerfile

$ docker build -f <Dockerfile name> .
$ docker build -f Dockerfile.dev .

## Using volumes to get the local changes in filesystem to be propagated inside the containers.

docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <container id>
$ docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app d5f67b4739b9

## Start a container in interactive mode

$ docker run -it -p <local machine port>:<containers port> <CONTAINER_ID>
$ docker run -it -p 3000:3000 <8e987b008902>

Visit in the browser: http://localhost:3000

# Development using docker-compose cli

## Build and run the app

$ docker-compose up --build
