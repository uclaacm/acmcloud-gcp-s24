
# Week 2: Intro to Google Cloud Platform

Link to Slides (Coming Soon!) and Recording (Coming Soon!)

# Google Cloud Storage CLI Guide

This guide provides an overview of how to use the Google Cloud Command Line Interface (CLI) to interact with Google Cloud Storage (GCS). GCS is a scalable object storage service that allows you to store and retrieve data from anywhere on the internet.

## Prerequisites

- A Google Cloud account. If you don't have one, you can sign up for a free trial [here](https://cloud.google.com/free). Note that although you may need to add a payment card, **you will not be charged unless you explicitly upgrade your account** as per the [docs](https://cloud.google.com/free/docs/free-cloud-features#:~:text=To%20complete%20your%20Free%20Trial,enable%20us%20to%20charge%20you.) - this requirement is largely to prevent spamming accounts.
- Google Cloud SDK installed on your machine. Follow the installation instructions [here](https://cloud.google.com/sdk/docs/install).

## Authentication

Before you can interact with GCS, you need to authenticate your Google Cloud account. Open your terminal and run:

```bash
gcloud auth login
```

A browser window will open for you to log in with your Google Cloud account and grant the necessary permissions. Once you've successfully logged in, you'll see a confirmation message in your terminal.

## Creating a Bucket

Buckets are the basic containers that hold your data in GCS. To create a new bucket, use the `gsutil mb` command:

```bash
gsutil mb gs://your-bucket-name
```


Replace `your-bucket-name` with a unique name for your bucket. Bucket names must be globally unique across all GCS users.

## Uploading Files

To upload a file to your bucket, use the `gsutil cp` command:

```bash
gsutil cp path/to/your/file.txt gs://your-bucket-name
```

Replace `path/to/your/file.txt` with the path to the file you want to upload.

## Listing Files

To list the files in your bucket, use the `gsutil ls` command:

```bash
gsutil ls gs://your-bucket-name
```

## Downloading Files

To download a file from your bucket, use the `gsutil cp` command, reversing the source and destination:

```bash
gsutil cp gs://your-bucket-name/your-file.txt path/to/download/location
```

Replace `path/to/download/location` with the path where you want to download the file.

## Deleting Files and Buckets

To delete a file from your bucket, use the `gsutil rm` command:

```bash
gsutil rm gs://your-bucket-name/your-file.txt
```

To delete a bucket, first, ensure it's empty, then use the `gsutil rb` command:

```bash
gsutil rb gs://your-bucket-name
```

## Conclusion

You've now learned the basics of interacting with Google Cloud Storage using the Google Cloud CLI. For more advanced features and options, refer to the [official documentation](https://cloud.google.com/storage/docs). Now we'll be hosting a simple static html file as a website with Google Cloud Storage. All content in this (and subsequent) tutorials will be covered under the free tier.

## Getting Started with Google Cloud Platform

To get started you'll need ot navigate to Google Cloud's online [console](https://cloud.google.com/) and create an account (just like the previous part). After creating your account, let's explore the platform

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
Coming soon!


