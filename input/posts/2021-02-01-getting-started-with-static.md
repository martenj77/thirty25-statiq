---
title: Getting started with Statiq
description: Your first steps with Statiq.Web?
date: 2021-02-01
image: ../assets/gettingstarted.jpg
tags: 
  - Statiq
---

I've been looking for a simple static site creator and since the very little programming knowledge I have is concentrated around C# and .NET I searched and found [Statiq.Web](https://statiq.dev/web/). With this post and some upcoming I'll try to describe what I did to get this blog up and running.

The plan is to document as the blog evolves. My overall plan is to break out of the [bootstrap theme that Statiq is bundled with](https://statiq.dev/web/themes/), moving over instead to [Tailwind CSS](https://tailwindcss.com/). Also I'll try and add some non-static functionality with Javascript working towards an API.

But I'm getting ahead of myself. First - let's show how I got the site initially set up.

## 1. Install .NET Core

This is outside the scope of this post, but I suggest you do the following

* install the .NET Core SDK from [dot.net](https://dot.net/) (prerequisite)
* install VS Code from [visualstudio.com](https://code.visualstudio.com/)

## 2. Create a .NET Core console application

Go to the folder you want to have your project folder in, i.e. `c:\repos`  or whatever.

Create a console application.

```ps
dotnet new console --name MyBlog
```

## 3. Install the latest version of Statiq.Web

Normally you just do `dotnet add package Statiq.Web`, but as it's in pre-release you have to specify the version as in the example below. 1.0.0-beta.19 is the latest version by this posts latest update (2021-02-01), but you could go to [Nuget/Statiq.Web](https://www.nuget.org/packages/Statiq.Web) to see what the latest version is.

Move to the project folder that was just created, `MyBlog` in the example, and then create a .NET Core console app

```ps
dotnet add package Statiq.Web --version 1.0.0-beta.19
```

## 4. Create a bootstrapper

Ok, you're quickly on your way to having your "hello world" up.

Now you need to set up a bootstrapper to set the instructions for the build.

Open `Program.cs` and remove all its contents and instead use this:

```csharp
using System;
using System.Threading.Tasks;
using Statiq.App;
using Statiq.Web;


namespace MySite
{
  public class Program
  {
    public static async Task<int> Main(string[] args) =>
      await Bootstrapper
        .Factory
        .CreateWeb(args)
        .RunAsync();
  }
}
```

During the course of your work with Statiq you'll edit this file much more, but this is a start.

## 5. Time to add some content

Yes, soon you'll get to build your first static output, hang on..

In the project root, add a folder called `input`. Inside this document, create a file called `index.md` with this content:

```markdown
Title: My First Statiq page
---
# Hello World!

Hello from my first Statiq page.
```

## 6. Time to run it

```ps
dotnet run -- preview
```

Once the build is done, fire up your browser and point it to http://localhost:5080.

Basically what has happened now is that your static site is in the folder `output` in the project's root. This can be moved and hosted on pretty much any web server.

This was very much a quick intro. We'll get to do more fun stuff in the coming posts..

---

### More on this topic

* [Deploying your Statiq site to Netlify](2021-02-01-setting-up-for-netlify)
