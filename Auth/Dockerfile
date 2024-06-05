FROM node:14
WORKDIR /i211110_backend
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 1110
CMD [ "node", "index.js" ]