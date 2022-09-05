# Welcome to the Anythink Market repo

To start the app use Docker. It will start both frontend and backend, including all the relevant dependencies, and the db.

Please find more info about each part in the relevant Readme file ([frontend](frontend/readme.md) and [backend](backend/README.md)).

## Development

When implementing a new feature or fixing a bug, please create a new pull request against `main` from a feature/bug branch and add `@vanessa-cooper` as reviewer.

## First setup

**[TODO 05/01/2018 @vanessa-cooper]:** _It's been a while since anyone ran a fresh copy of this repo. I think it's worth documenting the steps needed to install and run the repo on a new machine?_

What is Docker?
Docker is a free software developed by Docker Inc. It was presented to the general public on March 13, 2013 and has become since that day a must in the world of IT development.

It allows users to create independent and isolated environments to launch and deploy its applications. These environments are then called containers.

This will let the developer run a container on any machine.

As you can see, with Docker, there are no more dependency or compilation problems. All you have to do is launch your container and your application will launch immediately.

Steps to start with Docker:

1. Install Docker on your machine

2. Create your project

In order to create your first Docker application, I invite you to create a folder on your computer. It must contain the following two files:

A ‘main.py’ file (python file that will contain the code to be executed).
A ‘Dockerfile’ file (Docker file that will contain the necessary instructions to create the environment).
Normally you should have this folder architecture:

                         .
                         ├── Dockerfile
                         └── main.py
                         0 directories, 2 files

3. Edit the Python file

You can add the following code to the ‘main.py’ file:

         #!/usr/bin/env python3

         print("Docker is magic!")


Nothing exceptional, but once you see “Docker is magic!” displayed in your terminal you will know that your Docker is working.

3. Edit the Docker file
Some theory: the first thing to do when you want to create your Dockerfile is to ask yourself what you want to do. Our goal here is to launch Python code.

To do this, our Docker must contain all the dependencies necessary to launch Python. A linux (Ubuntu) with Python installed on it should be enough.

The first step to take when you create a Docker file is to access the DockerHub website. This site contains many pre-designed images to save your time (for example: all images for linux or code languages).

In our case, we will type ‘Python’ in the search bar. The first result is the official image created to execute Python. Perfect, we’ll use it!

# A dockerfile must always start by importing the base image.
# We use the keyword 'FROM' to do that.
# In our example, we want import the python image.
# So we write 'python' for the image name and 'latest' for the version.
FROM python:latest

# In order to launch our python code, we must import it into our image.
# We use the keyword 'COPY' to do that.
# The first parameter 'main.py' is the name of the file on the host.
# The second parameter '/' is the path where to put the file on the image.
# Here we put the file at the image root folder.
COPY main.py /

# We need to define the command to launch when we are going to run the image.
# We use the keyword 'CMD' to do that.
# The following command will execute "python ./main.py".
CMD [ "python", "./main.py" ]


4. Create the Docker image

Once your code is ready and the Dockerfile is written, all you have to do is create your image to contain your application.

$ docker build -t python-test . 
The ’-t’ option allows you to define the name of your image. In our case we have chosen ’python-test’ but you can put what you want.

5. Run the Docker image

Once the image is created, your code is ready to be launched.

$ docker run python-test

You need to put the name of your image after ‘docker run’.

There you go, that’s it. You should normally see “Docker is magic!” displayed in your terminal.

