    App name: Udagram
    Back-end API Environment:
        AWS Elastic Beanstalk Node.js 16 running on 64bit Amazon Linux Server
            URL - http://udagram-api-dev123.us-east-1.elasticbeanstalk.com/
            Environment includes Postgres database - endpoint: database-1.cmbtds0uf7ou.us-east-1.rds.amazonaws.com
            S3 bucket for uploading ebudacity app - elasticbeanstalk-us-east-1-602391567231

    Front-End:
        AWS S3 bucket: s3xudacity
            Configured for static website hosting: http://sangtt2.s3-website-us-east-1.amazonaws.com/

    Deployment Pipeline:
        CircleCI connected to main branch of GitHub project - https://github.com/thanhsang12t2/HostingAFullStackApplication
