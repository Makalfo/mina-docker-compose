# Example Mina docker-compose
Example Mina Docker Compose for Bringing Up the Mina Daemon with Mina Sidecar

## Description
The docker-compose file brings up the Mina Daemon with the docker image specified and the Mina Sidecar. Both docker containers are on it's own network called the mina-network. The configuration folder contains the mina-sidecar configuration file necessary for the delegation program.

# Configuration:
All configuration can be done in the .env file. <br>
 - `MINA_IMAGE`:         Docker image for the daemon <br>
 - `KEY_FOLDER`:         Folder containing the block producer hot key <br>
 - `WALLET_PASSWORD`:    Password for the wallet <br>
 - `COINBASE_RECEIVER`:  Coinbase Receiver for receiving the block production rewards <br>

# Instructions:
1) Populate the .env
2) Install docker and docker-compose using the script in the folder
   `sudo bash install_docker.sh`
3) Copy the key folder into the same directory as the docker-compose.yml, .env, and config folder
4) Ensure the permissions on the key folder and file. <br>
   `chmod 700 <key folder>` <br>
   `chmod 600 <key file>`
5) Bring up the containers via docker-compose <br>
   `docker-compose up -d`
   
# Notes
1) The docker logs can be viewed by the following:
   `docker logs -f mina-mainnet` <br>
   `docker logs -f mina-sidecar` <br>
2) Ensure the mina-sidecar is connected to the daemon as that's what reports the uptime. The mina-sidecar will show an error until the mina daemon is in bootstrap, catchup, or synced
