# Assignment 2
  - How to install Blue Ocean Plugin
  - Building a private GitHub Repository
  - Using Git SCM Poll
  - Post Build Actions - Extended Email Notification

# Installing Blue Ocean
-   Go to Manage Jenkins > Manage Plugins.
-   Choose the Available tab and search for blue ocean.
-   Select the Blue Ocean (BlueOcean Aggregator) plugin. The docs recommend installing only this one since all other Blue Ocean plugins will be installed -automatically (as dependencies).
-   Blue Ocean will be activated when Jenkins restarts.
-   Choose the Blue Ocean option from the left menu to use the Blue Ocean UI.

### Building a private GitHub Repository
-   Under Source Code Management select Git.
-   Add the private repository's URL in the Repository URL text box.
-   Since the repository is private, Jenkins will not be able to access the repo without credentials.
-   Click on Add button next to Credential text box. Choose Jenkins as the Credential Provider in the dropdown menu.
-   A popup should appear asking for the details.
-   Choose Username with Password under the Kind option. Enter GitHub username and password under their respective text boxes.
-   After adding your credentials choose the newly added credentials in the dropdown menu that appears next to Credentials label.
-   Now the private repository can be used with Jenkins like any other repository.

### Using Git SCM Poll

-  ##### Configuring build triggers
- - Map the Jenkins URL to a public IP address.
- - Map a Public IP to your Jenkins URL using ngrok.
- - Download and setup ngrok from : https://ngrok.com/download.
- - Run ./ngrock http 8080 (map your Jenkins port (8080) to a public IP. The public URL http://<foo>.ngrok.io should be used as the Webhook.

- ##### Setup
- - Navigate Settings -> Webhooks -> Add webhook in the repository.
- - Update the Payload URL to the Public IP http://<foo>.ngrok.io/github-webhook/.
- - Set Content type as application/json.
- - Update Which events would you like to trigger this webhook? as per requirement.
- - Ensure that the Active option is selected.

### Post-build Actions

- Select the project and navigate Configure -> Post-build Actions
- In Add post-build action choose Archive the artifacts.
- Mention the files to archive ( * to archive all the files).
- The Advanced settings can be used for specifying triggers.