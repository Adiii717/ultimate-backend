FROM node:12-alpine
# set our node environment, either development or production
# defaults to production, compose overrides this to development on build and run
ARG NODE_ENV=production
ENV NODE_ENV $NODE_ENV

RUN mkdir -p /nest


WORKDIR /nest
RUN apk add --no-cache git
RUN yarn global add @nestjs/cli
ADD package.json /nest
RUN yarn install --production=false
ADD . /nest
# Build production files
#RUN nest build proto-schema
#
#RUN nest build api-admin

# Bundle app source
COPY . .

EXPOSE 50020
CMD ["node", "dist/apps/api-admin/main.js"]
