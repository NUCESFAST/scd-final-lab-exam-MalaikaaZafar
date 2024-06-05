FROM node:14
RUN apt-get update && apt-get install -y curl
WORKDIR /i211110_frontend
COPY package*.json ./
RUN npm install -g npm-check-updates && ncu -u && npm install
RUN npm install -g serve
COPY . .
RUN npm run build
EXPOSE 3110
CMD ["serve", "-s", "build", "-l", "3110"]