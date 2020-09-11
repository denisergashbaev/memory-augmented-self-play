Setting up virtual environment 

cd memory-augmented-self-play
python3 -m venv venv
. venv/bin/activate
pip install wheel
pip install -r SelfPlay/requirements.txt

SETTING UP SOURCE FOLDERS FOLDER 
based on: https://binx.io/blog/2020/03/05/setting-python-source-folders-vscode/

contents of .vscode/settings.json: 
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

contents of .env: 
PYTHONPATH=${PYTHONPATH}:./SelfPlay