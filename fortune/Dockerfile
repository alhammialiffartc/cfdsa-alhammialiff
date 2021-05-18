#base image
FROM node:16

#define env var
ENV APP_ROOT=/app APP_PORT=3000

###BUILD IMAGE
#create the /app dir and cd into /app
WORKDIR ${APP_ROOT}

#at this pt, we're in APP_ROOT
ADD main.js .
ADD package.json .
ADD package-lock.json .
# copy these directories (directory cannot . ; must create public folder first)
ADD public public
ADD views views

### RUN IMAGE
#install the packages/libs in package.json (npm i or npm install same same)
RUN npm install

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/healthz || exit 1

# tells document that this container listens on port 3000
EXPOSE ${APP_PORT}

#run the application
ENTRYPOINT [ "node", "main.js" ]
