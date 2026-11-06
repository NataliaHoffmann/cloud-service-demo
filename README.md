<h1>Cloud Service Demo A1</h1>
<p>This site is built in COMP4312</p>
<p>Created by Natalia Hoffmann</p>

<h2>Project Purpose:</h2>
<p>The purpose of this project is to learn and demonstrate how to use Git, GitHub and Docker together in a cloud enviroment.</p>
<p>I used Git and GitHub to manage, track and publish the changes in my code, and I used Docker to package the application into a container.</p>

<h2>Included Files:</h2>
    <li>index.html: the webpage for the Cloud Service Demo</li>
    <li>README.md: The documentation file with the title, author and class code, as well as explaining the purpose of the project, included files, version control benefits and the difference between Docker image and Docker container.</li>
    <li>Dockerfile: The text file with instructions that Docker uses to build the container image.</li>

<h2>Version Control & Git & GitHub Benefits:</h2>
<p>Git and GitHub are complementary tools that have an important role in software development.</p>
    <li>Git is a version-control tool that runs locally on your computer, providing tools for tracking changes, managing project history, working offline and creating and merging branches.</li>
    <li>GitHub, on the other hand, is an online platform that hosts Git repositories and supports collaboration through cloud-based code storage and project management.</li>
<p>Together, they are essentials to protect developers from losing their work and allowing multiple contributors to work simultaneously without interfering with each other's contributions. Branches allow team members to develop different features independently and commits record changes and provide a history of the project's progress. These features help cloud and DevOps teams collaborate efficiently, manage code changes, and maintain an organized development process.</p>

<h2>Docker</h2>
<p>Docker is an open-source platform that automates the deployment, scaling, and management of applications inside lightweight, isolated packages called containers</p>
<p>Docker image is a read-only template that stores as a package, everything that the program needs to run: the code, libraries, dependencies and settings.</p>
<p>Docker container is the live version, runtime instance of a Docker image.<p>

<h2>How to run the application</h2>
<p>To build the Docker image using the Dockerfile: open your terminal and run the command:</p>
<code>docker build -t cloud-service-demo:1.0 .</code>

<br>
<p>To run the Docker Container run the command on your terminal:</p>
<code>docker run -d --name cloud-demo-container -p 8080:80 cloud-service-demo:1.0</code>