# A. SETUP

1. Setup Envrionment

``` bash
uv init
```

2. Create Virtual Environment
``` bash
uv venv
```

activate 
```bash
source ./.venv/bin/activate
```

3. Install Dependencies


``` bash
 uv add mcp[cli] requests

```

# MCP End-to-End Builds

**GOAL of Chess Stats**
- connect to chess.com api, get info from api about players, games, leaderboard etc
- Anyone who is connected to sever to ask various question / get info
- its all about chess & leveraging api that already exists and turn it into MCP server to interact with it 

- should work locally, but publish it so that anyone can download it,

- whenever we are interactin with MCP host / agent/ llm, we can ask this mcp server for it to track what we do and to save certain memories of what we do and recall it later

**CONCEPTS**
- tools, resources, prompts
- RAG -> easily save and retrieve data through embedding search

## MCP Server Build Chess Stats
1. create folder src/chess and three files under it
- __init__
- server
- chess_api
- test
2. edit the pyproject.toml so we can build the package and publish it to github
3. test package locally using claude, it won't work in vs code terminal bash
so in claude conig add 
``` json
"Chess Server": {
"command": "uv",
    "args": [
    "--directory",
    "/home/meklit/Documents/Udemy_mcp_training/mcp-build-chess-server",
    "run",
    "server.py"
    ]
}
```

in our .toml file, since we built the chess scrip, we don't have to specifiy server.py in config json, it will know when we reference chess
``` json
"Chess Server": {
"command": "uv",
    "args": [
    "--directory",
    "/home/meklit/Documents/Udemy_mcp_training/mcp-build-chess-server",
    "run",
    "chess"
    ]
}
```
- similar to doing `uv run chess`

4. check with questions in claude
"compare the ratings between hikaru and anthony levin"
5. deploy to github

## MCP Client Build Multi MCP Server 