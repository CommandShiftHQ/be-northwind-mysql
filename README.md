# Northwind MySQL Challenge

A pre-populated MySQL database and practice exercises.

## Getting Started

This exercise requires you to install docker on you macine. Docker allows us to run applications inside containers. You can read more about containers [here](https://www.docker.com/resources/what-container).

### Installing Docker

#### Ubuntu

Update your software database:
```
sudo apt update
```

Remove any old versions of docker that might be on your system:
```
sudo apt remove docker docker-engine docker.io
```

Install docker:
```
sudo apt install docker.io
```

Check docker version:
```
docker --version
```

#### Windows and Mac

Docker requires a Linux kernal in order to run. This can be emulated on Windos and Mac. The easiest way to do this is to install [Docker Desktop](https://docs.docker.com/get-docker/). You will need to have Docker Desktop running in order to use docker commands in your terminal.

### Install MySQL Workbench

For this challenge we will be using MySQL Workbench. Windows and Mac users can download it from [here](https://dev.mysql.com/downloads/workbench/). Linux users can run:

```
sudo apt install mysql-workbench
```

### Getting the Database Running

Run the container
```
docker run -d -p 3307:3306 --name northwind -e MYSQL_ROOT_PASSWORD=supersecret mcrcodes/northwind
```

Finally you can confirm the container is built and running by opening a shell inside it. This uses the `exec` command:
```
docker exec -it northwind bash
```

The -it option asks docker to open an interactive shell, and then we set the terminal promt to bash.

From here we can open mysql and check the database has been created:

```
mysql -uroot -p
```
You will then be prompted for the root user password. Type in `supersecret` and hit return. (characters you entered won't be shown on terminal, just type away and hit enter)

Check database has been created:
```
show databases;
```

You should see the following:
```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| northwind          |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)
```

That's everything we need to do inside the container. Type in `exit;` to close `MySQL` and then again (without the `;`) to exit the container. It will continue to run in the background.

## Working on the database

Open up MySQL-Workbench and connect it to `local instance 3303` if it's listed under "MySQL connections”.You will need to enter the root user password `supersecret`.

If the connection is not automatically shown, you can create one by clicking the `+` button and filling the fields:

	- Connection Name: `northwind`
	- Username: leave it as `root`
	- Port: leave it as `3307`
	- Password: `supersecret`

Click `Test Connection` and then `OK`.

In the bottom right of the screen you will see the `northwind` database. Right click on it and set it as your default schema.

Check that you are able to send queries to the database by entering some thing like:

```
SELECT * FROM employees;
```

Click the lightning bolt and confirm that the query returns employee information. 

## Running the image on M1 Mac

Start by cloning this repository on your local machine. Once cloned, `cd` into the main folder `cd northwind-mysql`. 

### Build and tag the image

Run the following command in your terminal. This will create a new northwind Docker image available for your M1 Mac.

```bash
docker build -f ./M1/Dockerfile . -t mcrcodes/northwind:m1
```

### Run the image

```bash
docker run -d -p 3307:3306 --name northwind -e MYSQL_ROOT_PASSWORD=supersecret mcrcodes/northwind:m1
```

Please ignore the `MYSQL_ROOT_PASSWORD` environment variable we passed above.

### Accessing the database

You can connect `MySQL Workbench` or any other DB GUI to this version of the database with the following settings:

```
- Username: user
- Port: 3307
- Password: password
```
