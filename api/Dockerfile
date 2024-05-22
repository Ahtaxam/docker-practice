FROM node:17-alpine


# Install nodemon globally
RUN npm install -g nodemon

# In a Dockerfile, the WORKDIR instruction sets the working directory for any command that follows it in the Dockerfile.
# This means that any commands that are run  will be executed relative to the specified directory.

# This instruction tells Docker to set the working directory  to /app . 
# Any subsequent commands in the Dockerfile, such as COPY, RUN etc... will be executed in this directory.
WORKDIR /app


# Everytime we build image whole our application code will copied into container even if we change one line
# so for cache purpose that image that less time to create we first copy package.json file (maybe) we install any package
# then we will install dependencies


# copy package.json file
COPY package.json .

# install dependencies
RUN npm install


# copy our source code to container
# first . is source as our dockeFile and code are in same folder
# second . is destination , paste our code at app directory of docker image
COPY . .


# run this command to install necessary dependencies listed in package.json file as we have copied code in previous layers
# so all dependencies will be installed in image.
# “RUN” instruction to execute commands that will run during the image build process
RUN npm install


# Use the EXPOSE command to tell Docker which ports the container will listen on at runtime.
EXPOSE 4000


# In a Dockerfile, the CMD instruction sets the command that will be executed when a container is run from the image
# CMD [ "node", "app.js" ]
CMD [ "npm" , "run", "dev"]