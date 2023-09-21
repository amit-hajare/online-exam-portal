FROM node:14

WORKDIR /usr/frontend

COPY . .
RUN rm -rf node_modules/ package-lock.json
RUN npm cache clean --force
RUN npm install

RUN npm run build

CMD ["sh", "-c", "npm start"] 

