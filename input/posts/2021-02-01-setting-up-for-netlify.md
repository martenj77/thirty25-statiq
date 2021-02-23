---
title: Deploying your Statiq site to Netlify
description: A quick and dirty way to host your hello world for the world (hello!) to see
date: 2021-02-01
image: ./assets/helloworld.jpg
tags: 
  - Statiq
---

This is the first part of (at least) two where we look at getting your site hosted at www.netlify.com.

## 1. Pre-requisites

* an initial setup of Static.Web, see [Getting started with Static](2021-02-01-getting-started-with-static)
* an Github account
* an Netlify account

## 2. Pushing it to Github

I'll cover this part in a separate post. Soon.

## 3. Setting up Netlify

* Go to and login in to www.netlify.com.
* From the app.netlify.com dashboard, click **New site from Git**.
* On the next screen, choose your git provider. In this example that would be **GitHub**.
* Now you need to authorize to GitHub, and after that you'll be presented  with a search for repositorys to link to Netlify. Most likely you don't see your new blog repo there, click **Configure the Netlify app on GitHub**
* Pick your repo
* Set the Branch to deploy to **master**
* Skip **Build commands** for now, and set **Publish directory** to `output`
* Click **Deploy site**

In a few seconds it'll be up and running. 

Ok - so that was the really quick and dirty version. This means that you first have to build it locally and then push to GitHub. As soon as it's pushed to the master branch it will be deployed to Netlify. Neat!

We of course want to skip building it locally, just pushing the `input` folder and letting instead GitHub automatically build when pushed and after that deployed to Netlify automatically.

Yes - we'll get to that. But let's just celebrate for a second or two that our hello world "site" is live first.

..

..

..

...

Ok, done. Moving on.