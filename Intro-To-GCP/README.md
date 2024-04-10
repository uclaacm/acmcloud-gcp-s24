
# Week 2: Intro to Google Cloud Platform

Link to Slides (Coming Soon!) and Recording (Coming Soon!)

In this tutorial, we'll be creating a Google Cloud Platform account, and hosting a simple static html file as a website with Google Cloud Storage. All content in this (and subsequent) tutorials will be covered under the free tier.

## Getting Started with Google Cloud Platform

To get started you'll need ot navigate to Google Cloud's online [console](https://cloud.google.com/) and create an account. Note that although you'll need to add a payment card, **you will not be charged unless you explicitly upgrade your account** as per the [docs](https://cloud.google.com/free/docs/free-cloud-features#:~:text=To%20complete%20your%20Free%20Trial,enable%20us%20to%20charge%20you.) - this requirement is largely to prevent spamming accounts. After creating your account, let's explore the platform

1. After verifying your account and signing in click `Console` to access GCP
2. Find the current project you're working in - *what is it called?*
3. Open the Cloud Shell - *what operating system is it running?*
4. Within the Cloud Shell, open the editor - although we won't be using it this in browser UI is a unique feature Google has over competitors like AWS
5. Try to find the Google Cloud Storage Product - there are a couple ways to do so!
6. Spend a couple minutes looking through the other products GCP offers - we'll ask if any seem interesting (and may cover them in later)

## Hosting a Static Files with Google Cloud Storage

Now that we've familiarized ourselves with the platform and power of Google Cloud a bit, let's deploy our first project: hosting a website! We've included a couple simple website files in this repo - but feel free to be creative and make your own (if you're familiar with React - you can also build and host a static React site, but will need a custom domain)! 

1. Navigate to the Google Cloud Storage page
2. Click on **Create a Bucket**
3. Give the bucket a name and click **Continue** to leave all other settings as default
4. Click on the bucket name to open it's page 
5. Under the **Permissions** remove public access restriction by clicking **Remove public access prevention** if the option is available
6. Under the same page grant the **Storage Object Viewer** role to **allUsers**
7. Finally, upload the static website files. Under **Objects**, click on the relevant file and on **Public URL** to view the website!

The above steps were adapted from google's official [documentation](https://cloud.google.com/storage/docs/hosting-static-website)

## Additional Resources
* 
