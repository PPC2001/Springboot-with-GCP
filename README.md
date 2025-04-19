CI/CD Pipeline Summary: Spring Boot on Google Cloud Run
-----------

1. Objective
Set up a fully automated CI/CD pipeline for a Spring Boot (Java 17) application deployed on Google Cloud Run, triggered on every Git push.
----------
2. Key Components
✅ GitHub – Source code repository
✅ Google Cloud Build – CI/CD automation
✅ Cloud Run – Serverless deployment
✅ Container Registry (GCR) – Docker image storage
✅ Service Account – Secure permissions for automation
---------------
3. Steps Performed
A. Application Setup
Created a Spring Boot (Java 17) app with a simple REST endpoint.

Configured Maven (pom.xml) for building the JAR.

Added a Dockerfile to containerize the app.

B. Google Cloud Setup
Enabled APIs: Cloud Build , Cloud Run , Container Registry

Created a Service Account (cloud-build-deployer) with required roles: Cloud Build Editor ,Cloud Run Admin ,Service Account User ,Storage Admin

C. CI/CD Pipeline (Cloud Build Trigger)
1. cloudbuild.yaml – Defined build steps:
2. Maven build (mvn clean package)
3. Docker build & push to Google Container Registry (GCR) :

![image](https://github.com/user-attachments/assets/1bb22715-4f1b-4195-b4d1-64f4f2e1571b)


4. Deploy to Cloud Run (serverless)

5. Configured GitHub Trigger:

![image](https://github.com/user-attachments/assets/bc7b6a22-b2ac-49aa-a10f-0800099cb359)


6. Auto-triggers on git push to main branch

7. Uses the service account for secure deployments:

![image](https://github.com/user-attachments/assets/606d8968-9b8a-4925-a427-cfcaee2f007a)


![image](https://github.com/user-attachments/assets/88656acf-166a-413c-bfbf-9adc64b2238b)


D. Deployment & Verification
Successfully deployed to: https://springboot-cloudrun-785428287445.us-central1.run.app/

![image](https://github.com/user-attachments/assets/b61f1a48-f93b-4ff2-932d-d46d7fd514b8)


![image](https://github.com/user-attachments/assets/088b5abb-c484-41ef-8cb9-4e0c05689296)

---------------

Automatic updates on every new push to GitHub.

4. Key Takeaways
✔ Zero manual deployment – Fully automated on Git push
✔ Serverless & scalable – Runs on Cloud Run
✔ Secure – Uses least-privilege service accounts
✔ Fast & efficient – Docker caching + Cloud Build speed

5. Future Improvements
Add testing stage (unit/integration tests)
Multi-environment (dev/staging/prod) with approvals
Monitoring & alerts (Cloud Logging + Error Reporting)

