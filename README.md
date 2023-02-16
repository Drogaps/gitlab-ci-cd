This pipeline helps speed up the process of building, continuous integration, and deployment of Android builds to Firebase environments. The build and tests are based on the Gradle build system.

The pipeline is triggered by a tag on the commit, which also determines the type of build. Initially, we define 3 environments for building and deploying (in my case release/debug/production). We also connect a cache, which will later speed up our pipeline.

Tags: build_d, build_p, build_r

####Stages:
![](https://https://github.com/Drogaps/gitlab-ci-cd/img/pipe.png)

*Slack_start:*
We then send a message to Slack via webhooks to start the build.
![](https://https://github.com/Drogaps/gitlab-ci-cd/img/start.gif)
Lint: Then we use the app: lint module to run the tests. And then we start a unit

Build: We add the build to the artifacts for easy management.

Deploy: We set the storage time for the artifacts, which we only need now. We export the credentials needed for Firebase and deploy.

Notify success: We output information about the deployed build to Slack, output project, workflow, date, version, author and a link to the build.
![](https://https://github.com/Drogaps/gitlab-ci-cd/img/final.gif)
Notify failed: We handle the situation if the pipeline fails somewhere. It also informs in the slack and gives a link to the pipeline for convenience.
![](https://https://github.com/Drogaps/gitlab-ci-cd/img/failed.gif)
