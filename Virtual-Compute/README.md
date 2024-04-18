
# Week 2: Intro to Google Cloud Platform

Link to Slides (Coming Soon!) and Recording (Coming Soon!)

## Running a Custom Website Locally

In this demo we will be deploying a simple website using React and Google's Compute Engine service. Before beginning, be sure to install [Node](https://nodejs.org/) and a [text editor](https://code.visualstudio.com/) of your choice. For this tutorial, we'll be using React to create a website - to follow along, either clone this repo or follow the steps below

1. Run the command `npm create vite@latest` in your project directory
2. Give your project a name when prompted (ex: ec2-react-demo)
3. Select `React` as the project framework
4. Select `JavaScript` as the framework variant

After acquiring the site code, you'll need to run `npm install` to install the site dependencies. Finally, to test the site locally, run `npm run dev` and navigate to the link provided (CTRL + Click).

## Deploying with Google Compute Engine

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