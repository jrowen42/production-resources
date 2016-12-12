---
layout: default
title: Oriole Guidelines and Resources
---

# O'Reilly Oriole Author Guide to Working with Atlas and LaunchBot

Oriole is a unique new medium that blends code, data, text, and video into a narrated learning experience with executable content.

To learn more and see examples, please go <a href="http://www.oreilly.com/oriole/">here</a>. Safari members can also see the complete collection <a href="https://www.safaribooksonline.com/oriole/">here</a>.

## Installation and Configuration

<div data-type="note">
  <p>The following instructions are for Mac. For those Windows users, we're sorry! Please reach out to us directly for help.</p>
</div>

## Make sure Git is installed

<div data-type="note">
  <h5>Why do you need Git?</h5>
  <p>An Oriole is more like software than a manuscript, and Git provides version control and useful tools such as branching, merging, and diffing.</p>
</div>

To check whether you have Git installed already, type `git` at the command line in a terminal window. If you see output that describes common Git commands, you have Git installed and can move on to Installing Docker for Mac.

Once Git is installed, use `git config` to specify your email address (you'll need to use the same email address you use to log in to Atlas, which we'll discuss below). [Here are instructions.](https://help.github.com/articles/setting-your-email-in-git/) It's important that you use the same email address here as you do in Atlas, so you'll be able to push changes to the remote Atlas repository.

## Install Docker for Mac

<div data-type="note">
<h5>Why do you need Docker?</h5>
  <p>Orioles run in secure, isolated containers that include all of the dependencies and libraries that the application needs to run. These dependencies are defined in a __Dockerfile__ that LaunchBot helps you create.</p>
</div>

If you already have Docker installed, please make sure it's updated to the latest version. Then skip to Get an Atlas account.

Docker is needed to build an Oriole, and "Docker for Mac" is an easy way to get Docker up and running on your Mac. [Follow the instructions here](https://docs.docker.com/docker-for-mac/) to download and install Docker for Mac.

## Get an Atlas account

<div data-type="note">
  <h5>Why do you need Atlas?</h5>
  <p>Well, to be honest, what you really need to use is Git. But Atlas makes it easy to get a Git repo and also makes it easy to add collaborators to work together on an Oriole project.</p>
</div>

We'll prepare a repo with a starter Oriole template for you and send you an invitaiton by email to join the Atlas project. If you haven't received an email invitation, please reach out to Eszti for help.

## Install LaunchBot

<div data-type="note">
  <h5>Why do I need to use LaunchBot?</h5>
  <p>LaunchBot helps you discover, build, and run Docker-enabled content, such as Jupyter Notebooks and Orioles. It provides a desktop GUI in place of the complex command-line process for installing and running applications. Think of LaunchBot as the place authors and editors will work together to create compelling text and runnable code, and as a tool that will help production ensure that all of the dependencies are captured in the Dockerfile so that the Oriole or notebook will run as expected.
</p>
</div>

Check out these “Getting Started” materials to learn more about LaunchBot and Oriole: 

* [LaunchBot Overview](http://launchbot.io/docs/overview/)
* [Benefits of Using LaunchBot](http://launchbot.io/docs/tutorial/benefits/)
* [Getting Started](http://launchbot.io/docs/tutorial/getting-started/)
* [Publishing Your Content](http://launchbot.io/docs/tutorial/publishing-content-to-launchbot/)
* [A Brief Introduction to Docker](http://launchbot.io/docs/tutorial/docker-intro/)
* [Creating an Oriole in LaunchBot](https://www.youtube.com/watch?v=WJMUkHzAFsg&feature=youtu.be)

1. Use Chrome or Firefox (Safari does not render correctly).
2. Sign up for a LaunchBot account at http://launchbot.io/. “Google sign up” is the easiest. If you decide to manually enter an email and password, you will need to verify your email (you'll receive a verification email) and then refresh the LaunchBot page to sign in.
3. Click “Download the latest release”.
4. Install via the command line. Prefix with `sudo` if the error message “Permission denied” is returned for the `unzip` command.
5. Start LaunchBot by typing `launchbot` at the command line. LaunchBot will start in your default browser (should be Chrome or Firefox).
6. The configuration page is found by clicking on the gear icon in the upper right section of the toolbar. Please check that autofill filled correctly.
   * *Launchbot Host:*<br/>Check that it is http://launchbot.io
   * *API Key:*<br/>Autofilled. You get a key when you sign up. It's on the launchbot.io page under Dashboard -> Profile. Copy/paste it here if not autofilled.
   * *Project Directory:*<br/>This is where LaunchBot will save local copies of projects, using Git. The default location is: `/Users/<your username>/launchbot`
   * *Path to Docker Executable directory:*<br/>Path to where Docker lives on your machine. The default is: `/usr/local/bin`
   * *Path to Git executable directory:*<br/>Use `which git` to find. Enter without the `git` ending. The default is: `/usr/bin/`
   * *Docker Host:*<br/>Autofilled. Should be: `unix:///var/run/docker.sock`
   * *Host IP Address*<br/>Autofilled. Should be: `0.0.0.0`
   * *CA Certificate:*<br/>Leave empty
   * *Certificate:*<br/>Leave empty
   * *Key:*<br/>Leave empty

# How to Make an Oriole with Git, Atlas, and LaunchBot

Now that al of the pieces are in place, we'll take you through the steps to start a new Oriole project.

In the following section, we'll show you how to:

* Find your new Atlas project, make a new branch, and clone that branch locally
* Verify that the container runs using LaunchBot + Docker
* Start authoring, making changes, and saving commits
* Push any committed changes back up to Atlas

### Pulling a project from Atlas

1. Sign in to Atlas. On your Projects dashboard, click on the project and then create a new branch. (Here's some [additional Atlas documentation](http://docs.atlas.oreilly.com/collaboration.html#adding-new-collaborators-YrTVuz), in case you need some help.). You'll need to create your own specific branch, as you cannot push directly to the master branch.
    1. On the Project page, click “Add a branch” (in green)
    2. Click “Create a branch” (Don’t worry about the warning that branching is in beta).
    3. The branch will be named with your username and a long number
2. Run Docker if it’s not already running. (When active, a whale icon will appear in your menu bar. Click on it to check Docker’s status.)
3. At the command line type `launchbot` at the terminal prompt and LaunchBot will open in your default browser (should be Chrome or Firefox).
4. In Atlas, under Projects, select the project you want to pull. Go to _Project Settings_ in the upper right. Copy the Git URL.
5. In LaunchBot, on the _Search_ page, paste the Git URL into the field labeled _clone an external project_ and download. The project will now appear under the _Projects_ page and a project directory will be made in `~/launchbot/<project name>`.
6. Exit LaunchBot (close the browser window) and return to the command line. You now need to switch to the branch you created in Step 1. ([Additional documentation on Git branches is available here](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging).)
    1. `cd ~/launchbot/<project name>`<br/>Change into the project directory. When you put the Git URL into launchbot in the last step, the project was automatically downloaded into the launchbot directory. `~/` stands for your home directory. For example, my home directory is `/Users/eschoell`, so my LaunchBot projects are under `/Users/eschoell/launchbot`, which is equivalent to `~/launchbot`. (LaunchBot created this directory for you when you first ran it.)
    2. `git fetch`<br/>This command will pull all the branches available, including the one you made.
    3. `git branch`<br/>This command will list the branches available. The starred one is the one you are currently on. At this point, it should be master.
    4. `git checkout <branch name>`<br/>This command will move you to your branch, which has your Atlas username followed by a large number.
    5. `launchbot`<br/>Start launchbot again
7. In LaunchBot, highlight the project and click _LAUNCH_
    1. Once launched, options will appear under a _Services_ tab. Most likely, this will say “Jupyter Notebook”. Click it.
    2. A window will open in your browser with the directory tree. Navigate to the notebook and open it. Any changes you make will be saved to your local repository.
    3. When you are done with edits, click `Command+S` to save any changes you made.
    4. Go back to the _Projects_ page and click “Stop”.
    5. Exit out of LaunchBot by closing the browser window.
    6. You can now commit the changes to the Atlas repo, outlined in Step 7.



### 


# Writing the Notebook Content

The text in the notebook isn’t intended to mirror the voice-over in the video—it's not meant to be a transcript. The text should be brief and stand on its own in case a viewer prefers to read through text+code instead of watching the video.

## Recording the Video

The video is intended to guide a viewer as they scroll down the page and try the code examples. It isn’t a mirror of the content, but should always refer to it.

## Introduction in the Video

The introduction should include:
* a brief bio about the author (1 min)
* explain the “big picture” of what the notebook demonstrates, and give a brief outline of what the viewer should expect from the lesson (aim for 1–2 minutes)

The Introduction is the only video segment shown in full-screen width, so it becomes the main opportunity to connect with the viewer; be casual, accessible, and human.

The remainder of the video (~25 minutes) will appear in a smaller window—unless required by the lesson. Body expressions should be BIG rather than small movements, so they get noticed. Even so, keep eye contact with the camera most of the time. The author stands behind their laptop while recording the video, to refer to the context of the text+code while working through the notebook.

Code won't execute automatically as the video plays, so the author should invite viewers to run the code, and even pause the video to experiment on their own with the examples.

It’s possible to enlarge the video in an Oriole on a cue, so the author can explain something outside of the screen. Ideally this would happen on a whiteboard or a large piece of paper. Whatever gets written should be large and simple enough to be read on a small screen.

When you finish a sentence, don’t just look down at the computer. Make a point to pause and smile, breathe, especially during the intro section. We need to plan for sync’ing video with the notebook.