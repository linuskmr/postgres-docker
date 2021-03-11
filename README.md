# postgres-docker

This is a docker-compose file which creates a docker container for a postgres database and one for pgadmin.

The [Installation and Usage](#installation-and-usage) section describes how to set up a sample database.

## Installation and Usage

Install [docker](https://docs.docker.com/get-docker/) and [docker-compose](https://docs.docker.com/compose/install/) on your computer.

Clone this repository and open a terminal in the repository's directory. Start the docker containers with:

```docker
docker-compose up -d
```

Open `localhost:9876` in your browser and login to pgadmin with user `user@domain.com` and password `SuperSecret`.

Now you should see the home screen of pgadmin. In the left sidebar right click on `Servers → Create → Server`. For `Name` choose anything you want, e.g. `db-server`. Click on `Connection` and type in `localhost` or your local network name / ip address for the host, `5432` for port, `admin` as username, `secret` as password and select `save password`.

Expand the `Servers` tab in the left sidebar and after that the `db-server`. Right click on `Databases → Create → Database`. Choose a name for the database like `sample-database` and click on `Save`.

Download and unzip a SQL dump on your computer named `sample-database.zip`.
Right click on `sample-database` in the left sidebar in pgadmin and choose `Restore`. Now click on the three dots in the filename input, click on the icon for `upload file`, upload the `sample-databas.backup`, close the upload window by clicking the x in the top right corner, choose `Probedatenbank.backup` and click `Select` and `Restore`.

Now you can expand `sample-database` in the left sidebar and go to `Schemas → public → Tables`. Now you can right click on a table and choose the `View/Edit Data` to get an overview over the table or select `Query Tool` to perform SQL Queries.

## Uninstall

Go the directory of this repository on your computer and stop the docker containers with:

```docker
docker-compose down
```

Find the container IDs for the images `dpage/pgadmin4` and `postgres`.

```docker
docker container ls -a
```

Delete the docker images using (change `PGADMIN_ID` and `POSTGRES_ID` with their actual ID's):

```docker
docker rm PGADMIN_ID POSTGRES_ID
```

