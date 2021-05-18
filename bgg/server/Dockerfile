FROM node:16

#define env var
ENV APP_ROOT=/app APP_PORT=3000
ENV BGG_DB_HOST=localhost BGG_DB_PORT=3306 BGG_DB_USER=root BGG_DB_PASSWORD=mypassword

WORKDIR ${APP_ROOT}

###Add items under /server dir
#Add directories
ADD bootstrap_public bootstrap_public
ADD bootstrap_views bootstrap_views
ADD lib lib
ADD public public
ADD views views

#Add items
ADD main.js .
ADD package.json .
ADD package-lock.json .

# Run npm to install libs
RUN npm install

# Healthcheck to check on container runtime status i think
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1 

EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js", "--html" ]