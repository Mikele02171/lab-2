    # we want image based on this image
    FROM node:18.16.0-alpine

    RUN apk add --no-cache tini
    RUN apk add --no-cache fortune
    #
    COPY --from=node:18.16.0-alpine /usr/local/bin/node /usr/local/bin/
    COPY --from=node:18.16.0-alpine /usr/local/lib/node_modules /usr/local/lib/node_modules
    #
    ENTRYPOINT ["/sbin/tini", "--"]
    CMD ["node", "-e", "console.log('tini is working correctly')"]


    # Create the app directory
    RUN mkdir -p /app
    WORKDIR /app

    # Copy package.json and install dependencies
    COPY package.json /app
    RUN npm --silent install

    # Move node_modules to a separate directory for shared usage
    RUN mkdir /deps && mv node_modules /deps/node_modules

    # Set environment variables
    ENV NODE_PATH=/deps/node_modules \
        PATH=/deps/node_modules/.bin:$PATH

    # Copy the application code
    COPY .. /app

    # Change ownership to the 'node' user
    RUN chown -R node:node /app /deps

    # Switch to the 'node' user
    USER node

    # Expose the application port
    EXPOSE 3000

    # Command to run the application
    CMD ["npm", "start"]