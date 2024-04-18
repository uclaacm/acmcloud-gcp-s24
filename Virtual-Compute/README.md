
# Week 3: Virtual Compute with Google Cloud

Link to Slides (Coming Soon!) and Recording (Coming Soon!)

## Running a Custom Website Locally

In this demo we will be deploying a simple website using React and either Google's Compute Engine or App Engine services. Before beginning, be sure to install [Node](https://nodejs.org/) and a [text editor](https://code.visualstudio.com/) of your choice. For this tutorial, we'll be using React to create a website - to follow along, either clone this repo or follow the steps below

1. Run the command `npm create vite@latest` in your project directory
2. Give your project a name when prompted (ex: ec2-react-demo)
3. Select `React` as the project framework
4. Select `JavaScript` as the framework variant

After acquiring the site code, you'll need to run `npm install` to install the site dependencies. Finally, to test the site locally, run `npm run dev` and navigate to the link provided (CTRL + Click).

## Deploying with Google Compute Engine

Below we'll outline the process of deploying your React site with Google's Compute Engine - a critical server based compute offering from Google. Pay attention to the specific configuration details and plethora of options provided to developers, as well as the relative complexity of working through configuration to App Engine.

1. Sign into the GCP portal in your browser
2. Navigate to the Compute Engine page
3. Create a new VM with the following settings
   * Region: us-west1
   * Machine configuration: E2, e2-micro
   * Allow HTTP traffic, Allow HTTPS traffic
4. SSH into the VM (simplest way is by clicking SSH -> "Open in browser window")
5. Run the following commands in the VM's terminal
```bash
sudo apt-get update
sudo apt-get install git

sudo mkdir /opt/nodejs
sudo curl https://nodejs.org/dist/v16.15.0/node-v16.15.0-linux-x64.tar.gz | sudo tar xvzf - -C /opt/nodejs --strip-components=1
sudo ln -s /opt/nodejs/bin/node /usr/bin/node
sudo ln -s /opt/nodejs/bin/npm /usr/bin/npm

sudo git clone https://github.com/uclaacm/acmcloud-gcp-s24.git
cd acmcloud-gcp-s24/Virtual-Compute
sudo npm install
sudo npm run dev
```
6. Navigate to the the external IP address in your browser (be sure to use http NOT https) - you should be able to see the React site live!

## Deploying with Google App Engine

Below we'll outline the process for deploying your same React website with Google's serverless App Engine service. Pay attention to the decreased customizability, but relative ease of deployment (the main tradeoff of serverless technologies)!

1. Sign into the GCP portal in your browser
2. Navigate to the App Engine page
3. Create a new application with the following details
   * Region: us-west2
   * Language: Node.js
   * Environment: Standard
4. Using the Cloud Shell, run the following commands
```bash
git clone https://github.com/uclaacm/acmcloud-gcp-s24.git
cd acmcloud-gcp-s24/Virtual-Compute/
npm install
npm run build

mkdir app_engine
cp -r dist/ app_engine/dist/
cd app_engine
```
5. Either through the commandline or browser IDE Create an `app.yaml` file in the `app_engine` folder
6. Paste the following content into the `app.yaml` file
```yaml
runtime: nodejs20
handlers:
# Serve all static files with url ending with a file extension
- url: /(.*\..+)$
  static_files: dist/\1
  upload: dist/(.*\..+)$
# Catch all handler to index.html
- url: /.*
  static_files: dist/index.html
  upload: dist/index.html
```
7. Return to the command line from step 4 and run `gcloud app deploy`
8. Finally, to view your site, navigate to the "Services" page under App Engine and select the app domain!

