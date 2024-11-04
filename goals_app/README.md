#

## Run mongodb in network

docker run --name mongodb --rm -d --network goals-net mongo

### RUn mongo with named volume

docker run --name mongodb -v data:/data/db --rm -d --n
etowrk goals-net mongo

### Run with secure env

docker run --name mongodb -v data:/data/db --rm -d --network goals-net \
 -e MONGO_INITDB_ROOT_USERNAME=hubert \
 -e MONGO_INITDB_ROOT_PASSWORD=secret \
 mongo

## Run backend in network

docker build -t goals-node .

docker run --name goals-backend -e MONGODB_USERNAME=hubert -e MONGODB_PASSWORD=secret --rm --p 80:80 -d --network goals-net goals-node

### Run backend with bind mounts

docker run --name goals-backend -v ${pwd}:/app -v /app/node_modules -v logs:/app/logs --rm --p 80:80 -d --network goals-net goals-node

## Run frontend in network

docker run --name goals-frontend --rm -d --network goals-net goals-react

### Run frontend with bind mount

docker run -v ${pwd}:/app/src --name goals-frontend --rm --p 3000:3000 -it goals-react
