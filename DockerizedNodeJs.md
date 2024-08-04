Here are the steps to build and run your Dockerized Node.js application:

1. **Navigate to your project directory**:
   ```bash
   cd fortune-cookie
   ```

2. **Build the Docker image**:
   ```bash
   docker build --tag=fortune-cookie .
   ```
   This command will build your Docker image and tag it as `fortune-cookie`.

3. **Run the Docker container**:
   ```bash
   docker run --rm -it --publish=3000:3000 fortune-cookie
   ```
    - `--rm`: Automatically removes the container when it exits.
    - `-it`: Runs the container in interactive mode.
    - `--publish=3000:3000`: Maps port 3000 of the container to port 3000 on your local machine.

4. **Open your browser** and visit:
   ```
   http://localhost:3000
   ```
   You should see the message "Hello World" displayed in your browser.
5. 