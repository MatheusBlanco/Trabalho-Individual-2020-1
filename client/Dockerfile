FROM node:14.15.1

RUN mkdir -p /client
WORKDIR /client

COPY package.json /client
COPY yarn.lock /client

RUN yarn install

COPY . /client

CMD ["yarn", "dev"]