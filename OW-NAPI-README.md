Creating an API for your OpenWhisk actions on Bluemix
---

Once the toolchain is installed, you will have 2 packages of Open Whisk actions one for development and one for production. You can view them in the [OpenWhisk dashboard on Bluemix](https://console.ng.bluemix.net/openwhisk/manage/actions). Each package has 5 actions that drive the recommendations aspect of the application.

![OpenWhisk Actions](docs/actions.png)

### Create API and Endpoints

To expose these OpenWhisk actions as a part of an API, we need to click the APIs link near the top of the Bluemix OpenWhisk interface. And then click on the Create an OpenWhisk API button.

*Note: we will focus on the production package in these steps. Once complete, repeat the steps for the dev package, prefixing names with `dev-` to dilineate.*

1. Create a name for your API. I chose `Acme Freight OpenWhisk API`

2. Click Create Operation button to begin adding your endpoints.

Name each endpoint to correspond with each OpenWhisk action. Choose Post as your Verb. Below is an example:

![Create operation endpoings](docs/endpoint-modal.png)

Repeat above to make an endpoint corresponding with each OpenWhisk action.

You're resulting page should look like the image below:

![API create](docs/create-api.png)

Scroll down

- Enable the "Require ... via API key" option; default options are suitable
- Make sure "Enable CORS..." option is checked
- Click Save button

![API save](docs/save-api.png)

### Create API Key

To create an API key, which is required to access the endpoints, click the "Sharing" link on the left of your screen shown below:

![Sharing](docs/sharing.png)

From this screen, click the "Create API Key" button.

In the Create API Key screen, do the following:

- Name your API key
- Take note of your API key
- Click the show checkbox and take note of your API key secret
- Click "Create":

![Create API Key](docs/create-api-key.png)

The last thing you'll need is the full path to your APIs, which you can find on the summary page (shown below as your 'Route'), along with all sorts of other useful information, including analytics:

![Summary](docs/summary.png)
