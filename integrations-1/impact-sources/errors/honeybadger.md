# Honeybadger

## About the integration

Honeybadger is a service that tracks your application errors. This integration allows Sleuth to track these errors to measure the impact your deploys make to the number of errors being generated.

It is assumed you already have an active Honeybadger account that is already tracking errors and outages on your application. \([Create a Honeybadger account](https://app.honeybadger.io/users/sign_up) if you don't have one.\) 

## Setting up the integration

To integrate Honeybadger as an error impact source in Sleuth: 

1. In the sidebar, click **Integrations**. 
2. Click the **Error Trackers** tab. 
3. In the Honeybadger tile, click **enable**. 
4. Enter your Honeybadger user API token. This token can be found in your Honeybadger user profile, under _Authentication_.   ![](../../../.gitbook/assets/honeybadger-api-token-request.png)   ![](../../../.gitbook/assets/honeybadger-api-token-location.png) 
5. Press **Save**. 

## Configuring the integration

Once the integration is successful, you will see an **Add impact** dropdown, along with the message **Honeybadger enabled** displayed in the tile. Select the Sleuth project you'd like to measure error impact on.   
 ![](../../../.gitbook/assets/honeybadger-enabled.png) 

Give this error tracking instance a **name** and select the **Honeybadger** **project** and **enviroment**. This information can be obtained in your Honeybadger account portal.  
 ![](../../../.gitbook/assets/honeybadger-sleuth-impact-info.png) 

That's it! Sleuth will now start verifying your deploys health by tracking the error counts from Honeybadger. Head over to the Dashboard to start seeing your data in action in the project and deploy health graphs.

## Removing the integration

#### If you wish to dissolve the Honeybadger integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Error Trackers**. 
2. In the Honeybadger integration card, click **disable**. The message **Honeybadger disabled** is displayed in the Honeybadger integration card once the integration is dissolved.

The Honeybadger integration is disconnected and no longer available to any projects within that organization. Any project-level modifications you made to the Honeybadger integration will be lost.

