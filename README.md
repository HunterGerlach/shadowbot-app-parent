# Shadowbot+AI App Parent

Quickstart - Click the following button to get started quickly (assuming you have credentials to the cluster)...

[![Contribute](https://www.eclipse.org/che/contribute.svg)](https://devspaces.apps.cluster-xcd89.dynamic.opentlc.com/#https://github.com/HunterGerlach/shadowbot-app-parent.git)

> Note: Update ^this^ badge with the URL for the cluster that Dev Spaces is deployed to if/when that changes.

This project was created as part of the Shadowbot+AI project.

It contains the configuration for an OpenShift Dev Spaces workspace, and includes another project.

The main components are:

- The Devfile - ./devfile.yaml
- The VSCode workspace - ./shadowbot.code-workspace

## Using this Project

### Day 0 - Planning your usage of Dev Spaces for Shadobot+AI

To properly use this repo, you'll need everything up and running. The [Day 0](docs/day-0-pre-reqs.md) docuemtation outlines the manual or automated steps necessary to get things properly configured. Once that's done you can come back here for Day 1 activities.

### Day 1 - Setting up the Repo

Now that you have an OpenShift cluster with a Dev Spaces CheCluster up and running, you'll need to setup secrets to be able to properly interact with the repo. These credentials will be used to commit your changes and pull changes made by others. You'll also need to setup your specific workspace for this project. All of those details are outlined in the [Day 1](docs/day-1-deployment.md) documentation. After you have completed those steps, return here to move on to normal contributing activity guidance.

### Day 2 - Contributing to this project

Now that everything is up and running, you should be able to do your daily development actvities like you would on any other machine. Additional contribution details can be found in the [Day 2](docs/day-2-contributing.md) documentation.

Happy coding...

> Test -> Code -> Refactor -> Commit -> Repeat.

## Useful links:

- Che blog: https://upstreamwithoutapaddle.com/blog%20post/2023/04/06/Development-On-OpenShift-With-Eclipse-Che.html

- Useful Video about OCP Dev Spaces: https://youtu.be/Jfd0F0-uYfU?si=PfR5_nXEYP12zrHG
