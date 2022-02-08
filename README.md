# Building and Running a Container

Go to the 'docker-node-hello-world' directory and run the following:

```
docker build -f Dockerfile -t hello-world:1.0 .
docker run -it --rm -p 4000:4000 hello-world:1.0
```
Now open your browser and go to "http://localhost:4000"

# Scanning a Container Image for Vulnerabilities

We will use [Trivy](https://github.com/aquasecurity/trivy) to scan the image you've created for Vulnerabilities:

```
trivy image hello-world:1.0
```
You should see many vulnerabilities:

![image](https://user-images.githubusercontent.com/3126261/152911159-aebab708-cb9f-4944-9361-9d1f704ce2ed.png)

To fix the vulnerabilities we will update the Base Image of the container image, build a new image and scan it.
Look at Dockerfile.fixed - it has a newer base image.
Let's now build and scan it

```
docker build -f Dockerfile.fixed -t hello-world:2.0 .
trivy image hello-world:2.0
```
As you can see - much less vulnerabilities now...
![image](https://user-images.githubusercontent.com/3126261/152911391-dd72a33d-50c4-4962-bb06-6f267678aea8.png)



