Architecture Diagram:
---------------------

![alt text](https://github.com/Machendra-org/Documentation/blob/c081c42d11815adb242501dab7e22640aeafaa23/Project%20Architecture.drawio.png?raw=)

Architecture Diagram Details:
-----------------------------

Step-1:
-------

For Example I take a NGINX is an Web Application

I write a Dockerfile this Web Application using some docker file Instractions like
- FROM
- WORDIR
- USER
- ENV
- RUN
- EXPOSE
- CMD
- ENTRYPOINT

Step-2:
-------

After Writting the Dockerfile I build an Image using below command

docker build -it <tagName> .

After Creating the Image and I Create Container using below command

docker run -d --name <ContainerName> -p <HostPort:ContainerPort> <ImageID>
I check here Container is running perperly or not and running fine 

Step-3:
-------

This Image I tag it, I push to the AWS ECR(Elastic Container regitry).

Step-4:
-------

Here I install the Helm Charts and I create helmchart of Daboya and I pull the Image from the ECR and apply image to the Helm chart 
I Deploy this Web Application using Below Helm Command.

- helm create Daboya
- helm ls
- helm repo 
- helm repo add <repoName>
- helm install
- helm upgrade
- helm rollback
