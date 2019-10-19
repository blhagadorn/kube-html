# Purpose
To create a simple HTML page on Kubernetes and make it publicly accessible via the internet

We will write index.html, publish it to GCR Docker repository, deploy it, and then expose to the internet via a service.

First, create a simple webpage like referenced in index.html

Then create a simple Dockerfile with Nginx that copies files in your `/site` directory, place the index.html there.
Dockerfile:
```FROM nginx
EXPOSE 80
COPY ./site /usr/share/nginx/html ```


Then tag and push it with these commands, where glassy-proton-256222 is your own project ID.

`docker tag kube-html gcr.io/glassy-proton-256222/kube-html`

`docker push gcr.io/glassy-proton-256222/kube-html`

`kubectl create -f html-deployment.yaml`

`kubectl create -f service.yaml`
