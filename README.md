# Northwind MySQL Challenge

## Getting Started

This exercise requires you to install docker on you macine. Docker allows us to run applications inside containers. You can read more about containers [here](https://www.docker.com/resources/what-container).

### Installing Docker

#### Ubunut

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

Clone this repo:
```
git clone https://github.com/MCRcodes/northwind-mysql.git
```
To make sure the docker image we are building is named correctly, we have written a `build` and `run` script.

To run the build script:
```
cd northwind-mysql

sh ./build.sh
```

Once this completes you can use the run script to start the container:
```
sh ./run.sh
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
You will then be prompted for the root user password. Type in `supersecret` and hit return.

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
| company            |
| mysql              |
| northwind          |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)
```

That's everything we need to do inside the container. Type in `exit` to close `MySQL` and then again to exit the container. It will continue to run in the background.
