<p align="center">
<img src="https://github.com/kura-labs-org/kuralabs_deployment_1/blob/main/Kuralogo.png">
</p>

## About

This project showcases the method to troubleshoot a problem between deployment. The user mistakenly deploys version 2 of an application that is still in testing stages instead of deploying version 1 of the application that is ready for production.

## Version 1

For steps and explanation regarding version 1, click [here](https://github.com/Jmo-101/Web_Hook_Flask/blob/main/README.md).

## Post Incident Report

### Reason

A new hire committed version 2 of the application to the main GitHub branch, which automatically triggered a build, test, and deploy to the production server. This action replaced version 1 of the application running on the server. The issue with version 2 of the application caused a 500 internal server error. The problem was located in the `application.py` file.

### Downtime

The downtime for the website during this error was approximately 20 minutes.

### Resolving

The steps taken to resolve this issue were as follows:

1. Checked the Jenkins log, but it showed that Jenkins deployed successfully without any issues.
2. Investigated the Elastic Beanstalk logs, as the problem was occurring there.
3. Found that line 20 in the `application.py` file was displaying an error related to how JSON code was written.
4. Corrected the issue by changing `JSON.loads` to `JSON.load`, as the Python script was supposed to read the document from the file.

### Resolved

After making the change to `json.load`, the application deployed successfully.

### Future Steps

For future incidents, consider the following steps:

- Consider rolling back to a previous version of the application. It would be faster to deploy a working version of the application rather than experiencing downtime on a server that needs to be up.




