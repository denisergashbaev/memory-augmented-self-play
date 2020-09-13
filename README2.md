# Project set-up in VSC 
# Virtual environment 

```bash
cd memory-augmented-self-play
python3 -m venv venv
. venv/bin/activate
pip install wheel
pip install -r SelfPlay/requirements.txt
```

# Pointing at source folders in VSC
based on: https://binx.io/blog/2020/03/05/setting-python-source-folders-vscode/

Adjust contents of `.vscode/settings.json` (or create new if does not exist): 
```json
{
    "python.pythonPath": "SelfPlay/venv/bin/python3",
    "terminal.integrated.env.osx": {
        "PYTHONPATH": "${workspaceFolder}/SelfPlay",
    },
    "terminal.integrated.env.linux": {
        "PYTHONPATH": "${workspaceFolder}/SelfPlay",
    },
    "terminal.integrated.env.windows": {
        "PYTHONPATH": "${workspaceFolder}/SelfPlay",
    },
    "python.envFile": "${workspaceFolder}/.env"
}
```
and contents of `.env` in root folder of the project (create one if does not exist): 
```bash
PYTHONPATH=${PYTHONPATH}:./SelfPlay
```
# How the project works 
Example of running mazebase. 
The root of the exutables is `SelfPlay` (we will assume it to be the working directory from now on)
run `mazebase_reinforce.py`. The file loads `config/config.cfg` using `utils/config.py#get_config()`. 

The config file defines such settins as `batch_size`, `num_epochs`, ...

It then executes `app/env_reinforce.py#run()`:
 * sets up the environment based on the config file `config/config.cfg`
 * selects the agent. In the case of running `mazebase_reinforce.py` it is going to be `agent/reinforce_agent.py`
 * gets an optimizer (it is going to be Adam in our case)
 * runs the episodes


