# Deploy your Firebase/React App on Netlify
You have a couple of options for deployment. You can either use Firebase hosting or deploy using Netlify. These are the instructions for Netlify. Firebase instructions are [here](https://github.com/nss-nightclass-projects/Night-Class-Resources/blob/master/book-3-data-driven-applications/chapters/firebase-deploy.md).


## Benefits of Deploying with Netlify
Netlify uses continuous deployment, which means when you push to your deployed branch, Netlify automatically deploys unless you change the settings. This means you can worry less about deploys and get detailed logs about your deploys, which are helpful if the deploy fails. Netlify will also NOT deploy the failed instance and will use the last successful deploy so you don't have to worry about your production app breaking. 

## Create the `.env` file
1. In the ROOT of your application, create a `.env` file
1. Place the following in that file with your keys as the values
```
REACT_APP_API_KEY=XXX
REACT_APP_AUTH_DOMAIN=XXX
REACT_APP_DATABASE_URL=XXX
REACT_APP_PROJECT_ID=XXX
REACT_APP_STORAGE_BUCKET=XXX
REACT_APP_MESSAGING_SENDER_ID=XXX
REACT_APP_APP_ID=XXX
REACT_APP_MEASUREMENT_ID=XXX
```

## Create the `apiKeys.js` file
1. Create `apiKeys.js` in your `helpers` directory.
1. Place the following in the file:
```
const firebaseConfig = {
  apiKey: process.env.REACT_APP_API_KEY,
  authDomain: process.env.REACT_APP_AUTH_DOMAIN,
  databaseURL: process.env.REACT_APP_DATABASE_URL,
  projectId: process.env.REACT_APP_PROJECT_ID,
  storageBucket: process.env.REACT_APP_STORAGE_BUCKET,
  messagingSenderId: process.env.REACT_APP_MESSAGING_SENDER_ID,
  appId: process.env.REACT_APP_APP_ID,
  measurementId: process.env.REACT_APP_MEASUREMENT_ID,
};

export default firebaseConfig;
```

## Let's Deploy!
1. Make sure all your code is pushed up to Github on the branch you want to deploy
1. Navigate to https://app.netlify.com/
1. Login/Create an account
1. Click "New Site from Git"

![screen shot](https://github.com/drteresavasquez/deploy-react-app-with-netlify/blob/main/Screen%20Shot%202020-11-09%20at%208.41.13%20PM.png)

5. Select Github or whichever tool you are using

![screen shot](https://github.com/drteresavasquez/deploy-react-app-with-netlify/blob/main/2.png)

6. Authorize Github if you have not already
7. Select the repo that you want to deploy

![screen shot](https://github.com/drteresavasquez/deploy-react-app-with-netlify/blob/main/3.png)

8. Update the settings as are shown below and click **Deploy Site**

![screen shot](https://github.com/drteresavasquez/deploy-react-app-with-netlify/blob/main/4.png)

## Update Environment Variables
Your deploy should have finished, but you will notice that your site page is empty and there are console errors.

1. Navigate to `settings` > `deploys` > `environment`
1. Add all the Environment variable keys and values as from your `.env` file as is shown below

![screen shot](https://github.com/drteresavasquez/deploy-react-app-with-netlify/blob/main/5.png)

## Redeploy
1. Navigate to `deploys` and select the **Trigger Deploy** dropdown to redeploy

![screen shot](https://github.com/drteresavasquez/deploy-react-app-with-netlify/blob/main/6.png)

## Update Firebase URL Settings
1. In Firebase under Authentication select sign in methods, scroll to Authorized domains. Add your Netlify URL. 

## Site should be good to go!
