# Project 5

- [Objectives](#Objectives)
- [Project Overview](#Project-Overview)
- [Part 1 - Semantic Versioning](#part-1---semantic-versioning)
- [Part 2 - Deployment](#Part-3---Deployment)
- [Part 3 - Diagramming](#Part-4---Diagramming)
- [Submission](#Submission)
- [Rubric](Rubric.md)

## Objectives

- Implement semantic versioning for images using `git tag` metadata in Actions
- Use `webhook`s to keep production up to date

## Project Overview

For this project you will be continuing to use your `cicd` repo made in project 4.

The documentation bullet points are written linearly.  As long as the information can be found, I am okay with you organizing it nicely.

## Parts & Milestones

Completion of each milestone **by the date specified for the milestone** will get you 5%
of extra credit per milestone date met. To qualify, you must submit your project on the milestone date to the Dropbox for Project 5 in Pilot.

All parts for the project are due 12/15

- [Part 1 - Semantic Versioning](#Part-1---Semantic-Versioning)
  - Milestone due 12/4
- [Part 2 - Deployment](#Part-2---Deployment)
  - Milestone due 12/11
- [Part 3 - Diagramming](#Part-3---Diagramming)
  - All parts are due 12/15
  - No EC

## Part 1 - Semantic Versioning

Right now, you likely `tag` the image with `latest`.  This means versions are never kept.  The solution we will use is to use `git` `tagging`.  A GitHub Action can use the metadata to generate a set of tags for an image.

### Tasks

- Practice creating `tag` for your `commit` using [semantic versioning](https://semver.org/)
- Amend your GitHub Action workflow to:
  - run when a `tag` is `push`ed
  - use the `docker/metadata-action` to generate a set of tags from your repository
  - push images to DockerHub with an image tags based on your `git` `tag` version AND `latest`

### Documentation

Create `README-CD.md` in main folder of your repo that details the following:

- CD Project Overview
  - (what are you doing, why, what tools)
- How to generate a `tag` in `git` / GitHub
- Behavior of GitHub workflow
  - what does it do and when
- Link to Docker Hub repository (as additional proof)

### Resources

- [GitHub - docker/metadata-action](https://github.com/docker/metadata-action)
- [Docker - Manage Tag Labels](https://docs.docker.com/build/ci/github-actions/manage-tags-labels/)

## Part 2 - Deployment

### Tasks

For this piece, use an EC2 instance.

- Install docker on the instance
- `pull` and `run` a container from your DockerHub image
  - confirm you can access your service running in the container from a browser
- Create a script to pull a new image from DockerHub and restart the container
  - put a copy of the script in a folder named `deployment` in your repo
- Set a listener / hook to receive messages using [adnanh's `webhook`](https://github.com/adnanh/webhook)
- Create a hook - when a message is received run the container restart script
  - put a copy of the hook configuration in a folder named `deployment` in your repo
- Configure either GitHub or DockerHub to send a message to the listener / hook

### Documentation

Update `README-CD.md` in main folder of your repo to include:

- How to install Docker to your instance
- Container restart script
  - Justification & description of what it does
  - Where it should be on the instance (if someone were to use your setup)
- Setting up a `webhook` on the instance
  - How to install [adnanh's `webhook`](https://github.com/adnanh/webhook) to the instance
  - How to start the `webhook`
    - since our instance's reboot, we need to handle this
- `webhook` task definition file
  - Description of what it does
  - Where it should be on the instance (if someone were to use your setup)
- How to configure GitHub OR DockerHub to message the listener 
- Provide proof that the CI & CD workflow work.  This means:
  1. starting with a `commit` that is a change, `tag`ing the `commit`, `push`ing the `tag`
  2. Showing your GitHub workflow returning a message of success.
  3. Showing DockerHub has freshly pushed images.
  4. Showing the instance that you are deploying to has the container updated.  
  
  Proof can be provided by **either** demonstrating to me in person OR by creating a *video* of the process.  If you go the video route and your file is too large for GitHub, submit it to the "Project 5 - Proof of Flow" Dropbox on Pilot

### Resources

- [Using GitHub actions and `webhook`s](https://levelup.gitconnected.com/automated-deployment-using-docker-github-actions-and-webhooks-54018fc12e32)
- [Using DockerHub and `webhook`s](https://blog.devgenius.io/build-your-first-ci-cd-pipeline-using-docker-github-actions-and-webhooks-while-creating-your-own-da783110e151)
  - Note: this has been the method focused on in lecture

## Part 3 - Diagramming

Include a diagram (or diagrams) of the continuous deployment process.  A good diagram will label tools used and how things connect.  This diagram would probably look best near your project description.

### Resources

You can use whatever tools you would like, here are some recommended tools that people use

- [Lucid Charts](https://www.lucidchart.com/pages/)
- [Textographo](https://textografo.com/)
- [Mermaid - new markdown feature](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/)
- [Eraser - Cloud Diagrams](https://docs.tryeraser.com/docs/cloud-diagrams)
- PowerPoint and OneNote are still good choices

## Submission

1. Commit and push your changes to your repository. Verify that these changes show in your course  
   repository.

Your repo should contain:
   - `README-CD.md` (and `README-CI.md` from P4)
   - `website` folder with website pages
   - `Dockerfile`
   - GitHub action `yml` file in `.github/workflows`
   - `deployment` folder with:
     - container restart script
     - `hook` definition file

2. In Pilot, paste the link to your project folder.


