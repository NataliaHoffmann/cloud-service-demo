<h1>Cloud Service Demo A1</h1>
<p>This site is built in COMP4312</p>
<p>Created by Natalia Hoffmann</p>

<h2>Project Purpose:</h2>
<p>The purpose of this project is to learn and demonstrate how Git and GitHub support version control, Docker packages an application into a container, and Kubernetes deploys the containerized application in a cloud environment.</p>
<p>I used Git and GitHub to manage, track, and publish changes to my code, Docker to package the application into a container, and Kubernetes to deploy and expose the application.</p>

<h2>Included Files:</h2>
<ul>
    <li>index.html: the webpage for the Cloud Service Demo</li>
    <li>README.md: The documentation file with the title, author and class code, as well as explaining the purpose of the project, included files, version control benefits and the difference between Docker image and Docker container.</li>
    <li>Dockerfile: The text file with instructions that Docker uses to build the container image.</li>
    <li>kubernetes/deployment.yaml: The Kubernetes Deployment configuration, that runs and manages the application Pod.</li>
    <li>kubernetes/service.yaml: The Kubernetes Service configuration, that exposes the application through a NodePort.</li>
</ul>

<h2>Version Control & Git & GitHub Benefits:</h2>
<p>Git and GitHub are complementary tools that have an important role in software development.</p>
<ul>
    <li>Git is a version-control tool that runs locally on your computer, providing tools for tracking changes, managing project history, working offline and creating and merging branches.</li>
    <li>GitHub, on the other hand, is an online platform that hosts Git repositories and supports collaboration through cloud-based code storage and project management.</li>
</ul>
<p>Together, they are essentials to protect developers from losing their work and allowing multiple contributors to work simultaneously without interfering with each other's contributions. Branches allow team members to develop different features independently and commits record changes and provide a history of the project's progress. These features help cloud and DevOps teams collaborate efficiently, manage code changes, and maintain an organized development process.</p>

<h2>Docker</h2>
<p>Docker is an open-source platform that automates the deployment, scaling, and management of applications inside lightweight, isolated packages called containers</p>
<p>Docker image is a read-only template that stores as a package, everything that the program needs to run: the code, libraries, dependencies and settings.</p>
<p>Docker container is the live version, runtime instance of a Docker image.</p>

<h2>Kubernetes</h2>
<h5>Pods vs Deployment</h5>
<p>A Pod is the smallest unit Kubernetes runs and contains one or more containers. A Deployment manages those Pods and make sure they keep executing replacing Pods if they fail or die.</p>
<h5>Purpose of a Kubernetes Service</h5>
<p>Kubernetes service provides a stable network for a group of Pods and routes traffic to them.</p>
<p>This project uses service.yaml to expose the application on port 30080 and forward traffic to port 80.</p>
<h5>Why might a cloud application need more than one Pod?</h5>
<p>Multiple Pods can handle more requests and improve availability if a Pod fails. This project's has one replica.</p>

<h2>How to run the application</h2>
<p>To build the Docker image using the Dockerfile: open your terminal and run the command:</p>
<code>docker build -t cloud-service-demo:1.0 .</code>
<p>To run the Docker Container run the command on your terminal:</p>
<code>docker run -d --name cloud-demo-container -p 8080:80 cloud-service-demo:1.0</code>

<h5>Run with Kubernetes and Minikube</h5>
<p>Start Minikube</p>
<code>minikube start --driver=docker</code>
<p>Load the image</p>
<code>minikube image load cloud-service-demo:1.0</code>
<p>Apply the Kubernetes Deployment and Service:</p>
<code>kubectl apply -f kubernetes/deployment.yaml</code><br>
<code>kubectl apply -f kubernetes/service.yaml</code>
<p>Forward the Service to port 8080 on your computer.</p>
<code>kubectl port-forward service/cloud-service-demo 8080:80</code>
<p>Keep this command running, then open <a href="http://localhost:8080">http://localhost:8080</a> on your preferred browser.</p>