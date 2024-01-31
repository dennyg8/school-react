# Dockerizing a React App using Vite

Requirements: have Docker and Node.js installed

## Create React app using Vite
    Create a folder for your React app, inside that folder open a terminal and write the command code . to open up vscode
    Inside vscode open a terminal (ctrl j) then type out these commands
        npm create vite@latest giesbrecht_dennis_site
        Select React and Typescript 
        cd giesbrecht_dennis_site 
        npm install
        npm run dev

    Now with all React app files created go into the vite.config.ts 
    Add this into the server function (inside the brackets {})
            host: true,     By setting host to true it allows the server to listen on all available interfaces making it accessible from outside the container
            port: 7775,     Vites default port is 5137, we can change this manually by inputing the port we want it to run on

## Create the docker file
    Create a docker file named Dockerfile inside the projects directory 
    Add these lines inside 
        FROM node:21
        WORKDIR /app
        COPY package.json .
        RUN npm install
        COPY . .
        EXPOSE 7775
        CMD ["npm", "run", "dev"]

    What this does it sets up a containerized Node.js environment, sets a working directory called app inside the container and copyies the local package.json to the container
    Then it installs the application dependencies, copies remaining files from local to the /app inside the container, sets up that the application inside the container uses port 7775
    Lastly it executes npm run dev to start the server
    Using Docker makes it easier to deploy consistantly across different environments

## Create the docker image and container
    To create a docker image and container you need to have docker running so launch the desktop application 
    Still inside the same Vscode terminal as before write these lines
        docker build -t giesbrecht_dennis_coding_assignment11 .             This builds a Docker image specifying the image name along with a "." indicating that the build context is in the current directory      

        docker run -p 7775:7775 giesbrecht_dennis_coding_assignment11       This runs a Docker container from a specified image. 7775:7775 maps the port inside the container to a port on the host machine

## Access the Web Application
    Input http://localhost:7775 in your browser
