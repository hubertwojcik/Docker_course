# Import Node Image from dockerHub
FROM node

# All the subsequents commands will be executed from inside that folder
WORKDIR /app

# First dot tells docker that all files and subfolder should be copied into image
# Second do path in image where the folders should bs stored
COPY . ./

RUN npm install

EXPOSE 80

CMD ["node","server.js"]