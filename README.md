# Shadowbot App Parent
This project was created as part of the Shadowbot project.

It contains the configuration for an OpenShift Dev Spaces workspace, and includes other projects.

The main components are:
- The Devfile - ./devfile.yaml
- The VSCode workspace - ./shadowbot.code-workspace

# Setup Instructions

OCP Dev Spaces

Follow Charro's blog
https://upstreamwithoutapaddle.com/blog%20post/2023/04/06/Development-On-OpenShift-With-Eclipse-Che.html

Steps:
- on RHPDS, create a cluster
- In the OCP web console, install the Dev Spaces operator
- Create an instance of the Dev Spaces
- Import the Che project (as a sample)
- Import the ShadowBot project

Notes:
- Do not use the DSC CLI.  Use the web UI
- If the devfile points to restricted github repo, then an OAuth ID is needed
	-> https://access.redhat.com/documentation/en-us/red_hat_openshift_dev_spaces/3.7/html/administration_guide/configuring-devspaces#configuring-oauth-2-for-github

Actions:
- Contact Hunter about the OAuth credentials for GitHub and eventualy GitLab
- Ask him how I was able to create the shadowbot-app-parent project in the restricted GitHub
- Set up another call w/ Charro 


# Recommendations and Best Practices

- OAuth is the recommended way to go regarding security and credentials.  Using ConfigMap and secrets is not as good. 
It just needs an admin to create clientID.
Useful link: https://access.redhat.com/documentation/en-us/red_hat_openshift_dev_spaces/3.7/html/administration_guide/configuring-devspaces#configuring-oauth-2-for-github

- Real-world scenario:  Delta airlines.
Tools used:
    - OAuth
    - GitLab
    - GitOps / Argo

- What kind of image to use for the Dev Spaces workspace?
    1- Using the default on, named "Universal Default Image". In that case, no need to have the `components` defined in the devfile.yaml.
        Pros: nothing to do
        Cons: large image (> 10GB)
    2- Build a custom image. The devfile.yaml file needs to include a component that points to the image to be used. For instance, the following one: quay.io/cgruver0/che/che-demo-app:latest.
    An environment variable `VSCODE_DEFAULT_WORKSPACE` with a value set to the desired workspace (eg `/projects/che-demo-app/che-demo.code-workspace`) needs to be added to the container for that component. If no custom image is being used, then this env variable cannot be set and when VSCode is started, an extra step is needed to click on "Open Workspace" (bottom-right of the IDE).    
    An example to build a custom image can be found here: https://github.com/eclipse-che-demo-app/che-demo-app/blob/main/images/build.sh
        Pros: 
            - smaller size
            - customized to the exact tools needed
        Cons: 
            - more steps to create and maintain the script
            - needs to be stored somewhere (Quay?)

- Automation
It is recommended to automate the provisionning of the Dev Spaces environments.  GitOps and Argo were used for Delta airlines.

- Requirements
An Openshift cluster needs to be available for the Dev Spaces setup

