This pipeline helps speed up the process of building, continuous integration, and deployment of Android builds to Firebase environments. The build and tests are based on the Gradle build system.

The pipeline is triggered by a tag on the commit, which also determines the type of build. Initially, we define 3 environments for building and deploying (in my case release/debug/production). We also connect a cache, which will later speed up our pipeline.

Tags: build_d, build_p, build_r

**Stages:**
![pipe](https://user-images.githubusercontent.com/40610049/219467585-8afc03e3-5a26-41d9-b713-8241ab25616c.png)


**Slack_start:**
We then send a message to Slack via webhooks to start the build.
![start](https://user-images.githubusercontent.com/40610049/219467257-a3f3b5b5-e626-4764-8925-cb6b49e77a77.gif)

**Lint:** Then we use the app: lint module to run the tests. And then we start a unit

**Build:** We add the build to the artifacts for easy management.

**Deploy:** We set the storage time for the artifacts, which we only need now. We export the credentials needed for Firebase and deploy.

**Notify success:** We output information about the deployed build to Slack, output project, workflow, date, version, author and a link to the build.
![final](https://user-images.githubusercontent.com/40610049/219467616-ad2e959b-a0d4-46d7-84a4-636ad66197f5.gif)

**Notify failed:** We handle the situation if the pipeline fails somewhere. It also informs in the slack and gives a link to the pipeline for convenience.

![failed](https://user-images.githubusercontent.com/40610049/219467643-83b5d51d-5656-4cfa-830e-c10136688af4.gif)

