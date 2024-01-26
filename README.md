Dockerizing a React App using Vite

# Requirements: have Docker and Node.js installed

## Create React app using Vite
    npm create vite@latest giesbrecht_dennis_site
    Select React and Typescript 
    cd giesbrecht_dennis_site
    npm install
    npm run dev

    Update vite.config file
        Add this into the server function
        host: true,
        port: 7775,

## Create the docker image and container
    docker build -t giesbrecht_dennis_coding_assignment11 .
    docker run -p 7775:7775 giesbrecht_dennis_coding_assignment11 

### Access the Web Application
    Input http://localhost:7775 in your browser
