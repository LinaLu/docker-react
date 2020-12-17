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

$ docker run <image id>

$ docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <container id>

$ docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app d5f67b4739b9

## Start a container in interactive mode

$ docker run -it -p <local machine port>:<containers port> <CONTAINER_ID>

$ docker run -it -p 3000:3000 <8e987b008902>

Visit in the browser: http://localhost:3000

# Development using docker-compose cli

## Build and run the app

$ docker-compose up --build

# Testing during development

# Run a test inide a running container

Start up a container and run tests inside that container.
docker run <image ID>
In another terminal:
docker exec -it <container ID> npm run test

# Using docker-compose cli

Configure the docker-compose.yml to run the test in a secondary container named tests.

docker-compose up --build

# Deployment

$ docker build -f deployment/Dockerfile .

Nginx loadbalancer default poty is 80. We need to map the ports in order to use nginx to serve static files.

$ docker run -p 8080:80 <image id>

Visit the app at http://localhost:8080/.

# Travis

The CI setup is trigger everytime we push to the github repo.
The output from the build would be available at https://travis-ci.com.
