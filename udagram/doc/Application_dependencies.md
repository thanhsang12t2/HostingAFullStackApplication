    AWS infrastructure requirements:
		AWS RDS instance running a Postgres database
		An AWS S3 bucket configured for Static Website Hosting to host the front-end webpage
    	AWS IAM user configured with permissions for deploying front and back-end applications
    	AWS Elastic Beanstalk Environment running Node.js 16

    Build & Deployment environment requirements:
    	AWS Elastic Beanstalk CLI to deploy the Back-end
		AWS CLI to deploy front-end
    	NodeJS 16.15

    For CI/CD Pipeline:
    	CircleCI project  connected to a GitHub repo
    	node, aws-cli, and aws-elastic-beanstalk orbs
