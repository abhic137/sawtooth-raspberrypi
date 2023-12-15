# sawtooth-raspberrypi
Running version of sawtooth on raspberry pi 4 arm64 version.
## Running the sawtooth with dev mode consensus
command
```
sudo sudo docker-compose -f raspberry-sawtooth-default.yaml up

```
for playing XO game:
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
