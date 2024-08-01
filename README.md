<p align="center">
  <img src="https://cdn-icons-png.flaticon.com/512/6295/6295417.png" width="100" />
</p>
<p align="center">
    <h1 align="center">CUSTOM-ELT-PROJECT</h1>
</p>
<p align="center">
		<em>Developed with the software and tools below.</em>
</p>
<p align="center">
	<img src="https://img.shields.io/badge/YAML-CB171E.svg?style=flat&logo=YAML&logoColor=white" alt="YAML">
	<img src="https://img.shields.io/badge/Python-3776AB.svg?style=flat&logo=Python&logoColor=white" alt="Python">
	<img src="https://img.shields.io/badge/Docker-2496ED.svg?style=flat&logo=Docker&logoColor=white" alt="Docker">
</p>
<hr>

##  Table of contents

> - [Overview](#overview)
> - [Repository Structure](#repository-structure)
> - [How It Works](#how-it-works)
> - [Getting Started](#getting-started)

## Overview

The CUSTOM-ELT-PROJECT is designed to simplify the process of extracting, loading, and transforming data between databases. Leveraging Docker and Python, this project provides a robust solution for data engineers and developers who need to manage and migrate data seamlessly.

## Repository Structure

1. **docker-compose.yaml**: This file contains the configuration for Docker Compose, which is used to orchestrate multiple Docker containers. It defines three services:
   - `source_postgres`: The source PostgreSQL database.
   - `destination_postgres`: The destination PostgreSQL database.
   - `elt_script`: The service that runs the ELT script.

2. **elt_script/Dockerfile**: This Dockerfile sets up a Python environment and installs the PostgreSQL client. It also copies the ELT script into the container and sets it as the default command.

3. **elt_script/elt_script.py**: This Python script performs the ELT process. It waits for the source PostgreSQL database to become available, then dumps its data to a SQL file and loads this data into the destination PostgreSQL database.

4. **source_db_init/source_init.sql**: This SQL script initializes the source database with sample data. It creates tables for users, films, film categories, actors, and film actors, and inserts sample data into these tables.

## How It Works

1. **Docker Compose**: Using the `docker-compose.yaml` file, three Docker containers are spun up:
   - A source PostgreSQL database with sample data.
   - A destination PostgreSQL database.
   - A Python environment that runs the ELT script.

2. **ELT Process**: The `elt_script.py` waits for the source PostgreSQL database to become available. Once it's available, the script uses `pg_dump` to dump the source database to a SQL file. Then, it uses `psql` to load this SQL file into the destination PostgreSQL database.

3. **Database Initialization**: The `source_init.sql` script initializes the source database with sample data. It creates several tables and populates them with sample data.

## Getting Started

1. Ensure you have Docker and Docker Compose installed on your machine.
2. Clone this repository.
3. Navigate to the repository directory and run `docker-compose up`.
4. Once all containers are up and running, the ELT process will start automatically.
5. After the ELT process completes, you can access the source and destination PostgreSQL databases on ports 5433 and 5434, respectively.