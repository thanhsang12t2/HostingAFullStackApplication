# Hosting a Full-Stack Application

In this project you will learn how to take a newly developed Full-Stack application built for a retailer and deploy it to a cloud service provider so that it is available to customers. You will use the aws console to start and configure the services the application needs such as a database to store product information and a web server allowing the site to be discovered by potential customers. You will modify your package.json scripts and replace hard coded secrets with environment variables in your code.

After the initial setup, you will learn to interact with the services you started on aws and will deploy manually the application a first time to it. As you get more familiar with the services and interact with them through a CLI, you will gradually understand all the moving parts.

You will then register for a free account on CircleCi and connect your Github account to it. Based on the manual steps used to deploy the app, you will write a config.yml file that will make the process reproducible in CircleCi. You will set up the process to be executed automatically based when code is pushed on the main Github branch.

The project will also include writing documentation and runbooks covering the operations of the deployment process. Those runbooks will serve as a way to communicate with future developers and anybody involved in diagnosing outages of the Full-Stack application.

# Udagram

This application is provided to you as an alternative starter project if you do not wish to host your own code done in the previous courses of this nanodegree. The udagram application is a fairly simple application that includes all the major components of a Full-Stack web application.



### Dependencies

```
- Node v14.15.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version

- npm 6.14.8 (LTS) or more recent, Yarn can work but was not tested for this project

- AWS CLI v2, v1 can work but was not tested for this project

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

```
### Installation

Provision the necessary AWS services needed for running the application:

1. In AWS, provision a publicly available RDS database running Postgres. <Place holder for link to classroom article>
1. In AWS, provision a s3 bucket for hosting the uploaded files. <Place holder for tlink to classroom article>
1. Export the ENV variables needed or use a package like [dotenv](https://www.npmjs.com/package/dotenv)/.
1. From the root of the repo, navigate udagram-api folder `cd starter/udagram-api` to install the node_modules `npm install`. After installation is done start the api in dev mode with `npm run dev`.
1. Without closing the terminal in step 1, navigate to the udagram-frontend `cd starter/udagram-frontend` to intall the node_modules `npm install`. After installation is done start the api in dev mode with `npm run start`.

### Preparing setting infrastructure for deployment
- Environment variables stored in AWS elastic beanstalk configuration
    - POSTGRES_USERNAME=postgres
    - POSTGRES_PASSWORD=15011993
    - POSTGRES_HOST=database-1.cmbtds0uf7ou.us-east-1.rds.amazonaws.com
    - POSTGRES_DB=postgres
    - AWS_BUCKET=arn:aws:s3:::sangtt2
    - AWS_REGION=us-east-1
    - AWS_PROFILE=default
    - JWT_SECRET=mysecretstring
    - URL=http://udagram-api-dev123.us-east-1.elasticbeanstalk.com/
- Environment variables for CI/CD stored in CircleCI Project Settings
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/ProjectSettingsCircleCI.png)
- Write to scripts of the project-level package.json file
    - "frontend:install": "cd udagram/udagram-frontend && npm install -f"
    - "frontend:start": "cd udagram/udagram-frontend && npm run start"
    - "frontend:build": "cd udagram/udagram-frontend && npm run build"
    - "frontend:test": "cd udagram/udagram-frontend && npm run test"
    - "frontend:e2e": "cd udagram/udagram-frontend && npm run e2e"
    - "frontend:lint": "cd udagram/udagram-frontend && npm run lint"
    - "frontend:deploy": "cd udagram/udagram-frontend && npm run deploy"
    - "api:install": "cd udagram/udagram-api && npm install ."
    - "api:build": "cd udagram/udagram-api && npm run build"
    - "api:start": "cd udagram/udagram-api && npm run dev"
    - "api:deploy": "cd udagram/udagram-api && npm run deploy"
    - "deploy": "npm run api:deploy && npm run frontend:deploy"    
### Configure the needed infrastructure for a web application
Screenshots
- Last successful CircleCi build
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/buildCircleCI.png)
- AWS RDS for the database overview
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/RDS.png)
- AWS ElasticBeanstalk for the (backend) API deployment
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/ElasticBeanstalk.png)
- AWS S3 for (frontend) web hosting
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/S3Bucket.png)
- Link to hosted api: http://udagram-api-dev123.us-east-1.elasticbeanstalk.com/api/v0/feed
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/api.png)
- Link to hosted front-end: http://sangtt2.s3-website-us-east-1.amazonaws.com
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/fontend.png)

### Write a proper pipeline file using the config.yml format used by CircleCi
https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/.circleci/config.yml

### Architecture diagram to document the deployment flow
- Development Pipeline Diagram
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/Pipeline.png)
- Infrastructure Diagram
![alt text](https://github.com/thanhsang12t2/HostingAFullStackApplication/blob/main/udagram/doc/screenshots/Infrastructure.png)

