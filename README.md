# sawtooth-raspberrypi
Running version of sawtooth on raspberry pi 4 arm64 version.
## Running the sawtooth with dev mode consensus
command
```
sudo sudo docker-compose -f raspberry-sawtooth-default.yaml up

```
### for playing XO game with Dev mode:
```
sudo docker exec -it sawtooth-shell-default bash
```
```
sawtooth keygen jack
sawtooth keygen jill
```
```
 xo create my-game --username jack --url http://rest-api:8008
```
```
xo list --url http://rest-api:8008
```
```
xo take my-game 5 --username jack --url http://rest-api:8008

```
```
xo take my-game 1 --username jill --url http://rest-api:8008
```
```
xo show my-game --url http://rest-api:8008

```

## Running Sawtooth with PBFT 
Command
```
sudo sudo docker-compose -f raspberry-sawtooth-pbft.yaml up
```
### playing the XO game with PBFT:
to get into the bash 
```
docker exec -it sawtooth-shell-default bash

```
to generate keys for jack and jill (2 players)
```
sawtooth keygen jack
sawtooth keygen jill
```
to create a game on node 0
```
xo create my-game --username jack --url http://sawtooth-rest-api-default-0:8008
```
Verify that the create transaction was committed by displaying the list of existing games:
```
xo list --url http://sawtooth-rest-api-default-0:8008
```
Start playing tic-tac-toe by taking a space as the first player, Jack. In this example, Jack takes space 5:
```
xo take my-game 5 --username jack --url http://sawtooth-rest-api-default-0:8008

```
Next, take a space on the board as player 2, Jill. In this example, Jill takes space 1:
```
xo take my-game 1 --username jill --url http://sawtooth-rest-api-default-0:8008
```
Whenever you want to see the current state of the game board, enter the following command:
```
xo show my-game --url http://sawtooth-rest-api-default-0:8008
```

result:
```
GAME:     : my-game
PLAYER 1  : 023d47
PLAYER 2  : 0265ef
STATE     : P1-NEXT

  O |   |  
 ---|---|---
    | X |  
 ---|---|---
    |   |  
```
to check the setting in the 0 node
```
sawtooth settings list --url http://sawtooth-rest-api-default-0:8008

```
Either player can use the xo delete command to remove the game data from global state.
```
 xo delete my-game --url http://sawtooth-rest-api-default-0:8008
```
To display the list of blocks of node 0 we can change the number from 0-4
```
sawtooth block list  --url http://sawtooth-rest-api-default-0:8008

```
To display more information about the block
```
sawtooth block show <BLOCK_ID> --url http://sawtooth-rest-api-default-0:8008

```
The sawtooth state command lets you display state data. Sawtooth stores state data in a Merkle-Radix tree (for more information, see Global State.

  Use sawtooth state list to display addresses in state with their size and associated data. The default output format truncates each line; use --format with csv, json, or yaml to display the entire line.
```
sawtooth state list --format csv --url http://sawtooth-rest-api-default-0:8008
```
Use sawtooth state show to view state data at a specific address (a node in the Merkle-Radix database). Copy the address from the output of sawtooth state list, then paste it in place of {STATE_ADDRESS} in the following command:
```
sawtooth state show {STATE_ADDRESS} --url http://sawtooth-rest-api-default-0:8008
```
