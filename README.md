# Fantasy Premier League API Pipeline

Technology used: Docker, Airflow, DBT, PostgreSQL, Python, Power BI

## Abstract

A data pipeline to extract data from Fantasy Premier League (FPL) API.

The goal was to create a Power BI report for my FPL team of 2023-2024 season using the FPL API. Airflow was used to orchestrate a pipeline that would extract data for my FPL, transform and store it in a postrgeSQL database and report on it in Power BI.

## Architecture

<img src="https://github.com/Sidkian/FPL-API-Pipeline/blob/main/images/FPL-Architecture.jpeg">

* [extract_FPL.py](https://github.com/Sidkian/FPL-API-Pipeline/blob/main/airflow/extraction/extract_FPL.py) extracts data from FPL API and performs basic transformations and stores it in a tmp folder
* [upload_postgeSQL.py](https://github.com/Sidkian/FPL-API-Pipeline/blob/main/airflow/extraction/upload_postgreSQL.py) creates database tables and loads the extracted data into PostgreSQL
* DBT models transform the raw data in PostgreSQL and generate data marts
* Data marts are used to create a [FPL Power BI Report](https://github.com/Sidkian/FPL-API-Pipeline/blob/main/powerbi/FPL.pbix)
* Airflow is used to run the python files and dbt models on a set schedule.
* Airflow and DBT are installed in docker containers

## Output

[FPL Power BI Report](https://github.com/Sidkian/FPL-API-Pipeline/blob/main/powerbi/FPL.pbix) visualizes the FPL data.
* Gameweek: Provides stats such as highest score, average score, captaincy, top scorer and chips used for the previous, current and upcoming gameweek
* Fixtures: Shows key fixtures and key players for the upcoming gameweek
* My Team: Provides stats such as current rank, total points and transfers made for my FPL team
* Team Transfers: Provides information on players transferred in and out of my FPL team and transfers made for the current gameweek and season 
* Transfer Planner: Shows key fixtures and players in the remaining gameweek as well as the fixture difficulty rating provided by FPL to plan out future transfers

<img src="https://github.com/Sidkian/FPL-API-Pipeline/blob/main/images/Gameweek.jpeg">

<img src="https://github.com/Sidkian/FPL-API-Pipeline/blob/main/images/Fixtures.jpeg">

<img src="https://github.com/Sidkian/FPL-API-Pipeline/blob/main/images/My-Team.jpeg">

<img src="https://github.com/Sidkian/FPL-API-Pipeline/blob/main/images/Team-Transfers.jpeg">

<img src="https://github.com/Sidkian/FPL-API-Pipeline/blob/main/images/Transfer-Planner.jpeg">

