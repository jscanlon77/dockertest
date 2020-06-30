# dockertest
dockertest

Ensure that we have hyper-v running in bios and on Windows, install Docker for Windows

# Directions to publish an angular application to docker
# And this command to push it

docker push docker.pkg.github.com/jscanlon77/dockertest/latest:0.0.1
https://medium.com/better-programming/7-steps-to-dockerize-your-angular-9-app-with-nginx-915f0f5acac

and hey presto we have created a docker image which we can access by localhost:8080 easily in a virtual container.

Create a Dockerfile in the angular application

FROM node:10.16.2-alpine AS builder
COPY . ./test-application
WORKDIR /test-application
RUN npm i
RUN $(npm bin)/ng build --prod
FROM nginx:1.15.8-alpine
COPY --from=builder /test-application/dist/test-application/ /usr/share/nginx/html

run - docker run --name ng-app-container -d -p 8080:80 test-application

# look at the image
docker image ls

# in github create a token which can be used to login via the angular cli command line to connect to github
docker login -u jscanlon77@googlemail.com -p <some token> docker.pkg.github.com
  
 # then issue the command to push the docker image
 docker push cd0faba930d0 docker.pkg.github.com/jscanlon77/dockertest/latest:0.0.1
 
 and then we're done..
 
 #Commands to start and stop docker images
 
 docker container stop <image_id> 
docker container rm <image_id>
