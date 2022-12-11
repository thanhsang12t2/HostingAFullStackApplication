    Pipeline process: Circle CI/CD connected to github repo: https://github.com/duyvien/HostAFullStackApplication

    Process:
    	Run Front-End install and Back-End install scripts to install   dependencies.
			API script: `cd udagram/udagram-api && npm install .`
    		Front-End script: `cd udagram/udagram-frontend && npm install -f`
    		
    	Run Front-end and Back-end build scripts to build app.
    		Back-End script: `cd udagram/udagram-api && npm run build`
			Front-End script: `cd udagram/udagram-frontend && npm run build`

    	Run Front-end and Back-end deployment scripts to deploy Back-end to AWS Elastic Beanstalk and Front-end to AWS S3 bucket.
			Back-End Script: `cd udagram/udagram-api && npm run deploy`
    		Front-End Script: `cd udagram/udagram-frontend && npm run deploy`