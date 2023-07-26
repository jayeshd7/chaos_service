# Defensive Demo
This DEMO project is used for running Chaos Experiment

## REST endpoints
- `/actuator/chaosmonkey` - Chaos Monkey for Spring Boot
- `/employee/all` - Return employees from DB (H2)

## Chaos Experiments
Mac : Set virtual environment in python and install `chaostoolkit-spring`
```
python3 -m venv ~/.venvs/chaostk
source  ~/.venvs/chaostk/bin/activate
pip install chaostoolkit-spring
```

Win : Set virtual environment in python and install `chaostoolkit-spring`
```
python3 -m venv {project_path}/.venvs/chaostk
source  {project_path}/.venvs/chaostk/scripts/activate
pip install chaostoolkit-spring
```

## Intall Chaos Toolkit
```
pip install chaostoolkit
```


Run the experiment:
`chaos run {path_of_experiement_folder}/experiments.json`

Output When Experiment is successful:
```
(chaostk)  chaostk > chaos run experiments.json
[2020-05-17 12:24:50 INFO] Validating the experiment's syntax
[2020-05-17 12:24:50 INFO] Experiment looks valid
[2020-05-17 12:24:50 INFO] Running experiment: Employee when database is down
[2020-05-17 12:24:50 INFO] Steady state hypothesis: Employee data is available
[2020-05-17 12:24:50 INFO] Probe: we-can-retrieve-employee-data
[2020-05-17 12:24:50 INFO] Steady state hypothesis is met!
[2020-05-17 12:24:50 INFO] Action: enable_chaosmonkey
[2020-05-17 12:24:50 INFO] Action: configure_assaults
[2020-05-17 12:24:50 INFO] Action: configure_repository_watcher
[2020-05-17 12:24:50 INFO] Steady state hypothesis: Employee data is available
[2020-05-17 12:24:50 INFO] Probe: we-can-retrieve-employee-data
[2020-05-17 12:24:50 INFO] Steady state hypothesis is met!
[2020-05-17 12:24:50 INFO] Let's rollback...
[2020-05-17 12:24:50 INFO] Rollback: disable_chaosmonkey
[2020-05-17 12:24:50 INFO] Action: disable_chaosmonkey
[2020-05-17 12:24:50 INFO] Experiment ended with status: completed

```

Output When Experiment is fail:
```
[2023-07-26 10:11:13 INFO] Validating the experiment's syntax
[2023-07-26 10:11:13 INFO] Experiment looks valid
[2023-07-26 10:11:13 INFO] Running experiment: Employee when database is down
[2023-07-26 10:11:13 INFO] Steady-state strategy: default                     
[2023-07-26 10:11:13 INFO] Rollbacks strategy: default                        
[2023-07-26 10:11:13 INFO] Steady state hypothesis: Employee data is available
[2023-07-26 10:11:13 INFO] Probe: we-can-retrieve-employee-data
[2023-07-26 10:11:15 INFO] Steady state hypothesis is met!
[2023-07-26 10:11:15 INFO] Playing your experiment's method now...
[2023-07-26 10:11:15 INFO] Action: enable_chaosmonkey
[2023-07-26 10:11:15 CRITICAL] Steady state probe 'we-can-retrieve-employee-data' is not in the given tolerance so failing this experiment
[2023-07-26 10:11:15 INFO] Let's rollback...
[2023-07-26 10:11:15 INFO] Rollback: disable_chaosmonkey
[2023-07-26 10:11:15 INFO] Action: disable_chaosmonkey
[2023-07-26 10:11:15 INFO] Experiment ended with status: deviated
[2023-07-26 10:11:15 INFO] The steady-state has deviated, a weakness may have been discovered

```
