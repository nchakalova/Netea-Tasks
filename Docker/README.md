# Containerized System with Frontend, MySQL, and MongoDB Containers

The PHP app connects to both DBs, reads dummy data, and then displays it. The system can be deployed and run on both Mac or Windows OS regardless of the version. The entire configuration is injected, and its possible to build both Production and Dev environment versions of the frontend container with PHP Xdebug turned on or off.

## Requirements

You'll need Docker, it can be downloaded from here: https://www.docker.com/products/docker-desktop

## Setup

1. Clone this repo on your local machine:

```bash
git clone https://github.com/elbaconslayer/Netea-Test.git
```

2. Navigate to the project dir:

```bash
cd Netea-Test
```

3. Create a .env file in the project dir:

```bash
touch .env
```

4. Add the following variables to the .env file:


```makefile
DB_HOST=db
DB_PORT=3306
DB_NAME=myapp
DB_USER=myuser
DB_PASS=mypass
MONGO_HOST=mongo
MONGO_PORT=27017
APP_ENV=dev
```

## You can change these values if you want to use a different DB name or credentials.


5. Build and start the containers for DEV:


```css
docker-compose build --build-arg APP_ENV=dev
docker-compose up
```

6. Build and start the containers for PROD:


```css
docker-compose build --build-arg APP_ENV=prod
docker-compose up
```
7. If the containers are in a running state, you can access the PHP app by opening a browser and navigating to **'http://localhost'**. The PHP app should display the dummy data retrieved from MongoDB and MySQL.


## Config
All configurations are injected, making it easy to make changes to the system.

To modify the DB settings, you can update the environment variables values in the **'.env'** file:

* **'DB_HOST'**: MySQL container hostname.
* **'DB_PORT'**: MySQL port number.
* **'DB_NAME'**: MySQL DB Name.
* **'DB_USER'**: MySQL username.
* **'DB_PASS'**: MySQL password.
* **'MONGO_HOST'**: MongoDB container hostname.
* **'MONGO_PORT'**: MongoDB port number.

To build a PROD or DEV version of the frontend container with PHP Xdebug, you can run **'--build-arg APP_ENV=prod'** or **'--build-arg APP_ENV=dev'** when running the **'docker-compose build'** command
