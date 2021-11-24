# Setting up (Old - should definitely work)

For now all compilation and installation steps are specified in the following [pdf](https://github.com/doctordeano/MotionInput/blob/main/version3.0/Compilation%20Instructions%20%26%20Libraries%20required.pdf)

This will hopefully change in future.

## Potential compilation errors & fixes
**Wrong opencv version**

It has been reported that the new opencv release causes a problem. Downgrade your opencv package to version 4.5.3.56.

**Missing python packages**

To fully compile and run the code you may also need to install other python packages:
- tabulate (install from the **command line with sudo/administrative privilages**)
- wmi
- imutils

# Setting up (New - dunno if works)

## Dependencies
There are a few things that you will need to install before proceeding

Visual Studio Build Tools 2019 - [Download](https://my.visualstudio.com/Downloads?q=build%20tools%202019&wt.mc_id=o~msft~vscom~older-downloads)

To test if visual studio build tools are installed correctly:

Run this in powershell

```
msbuild
```
You should get this
```
Microsoft (R) Build Engine version 4.8.4084.0
[Microsoft .NET Framework, version 4.0.30319.42000]
Copyright (C) Microsoft Corporation. All rights reserved.

MSBUILD : error MSB1003: Specify a project or solution file. The current working directory does not contain a project or solution file.
```

Pipenv - `pip install --user pipenv`

To test if pipenv was installed correctly:

Run this in powershell

```
pipenv --version
```
You should get something like this:
```
pipenv, version 2021.11.15
```

To install all dependencies navigate to the version3 folder run this:

```
pipenv install
```


# Branches

**We have 2 important branches:**
 - `main` - Main branch with a stable version of the code
 - `dev` - Development branch where all of our branches are merged first.

**When you are working on a specific task or a feature:**
 - Create a branch using one of those naming schemes:
   - Team branch: `groupnumber-task-name` (i.e. 14-hand-gestures)
   - Personal branch: `firstname-task-name` (i.e. adi-hand-gestures)
 - Commit your changes to your branch.
 - Make a pull request to the `dev` branch

# Pull Requests

When making a pull request follow the [PR-messages](#pr-messages) structure

Once you've made a pull request, you are not allowed to merge it by yourself.

Ask one of the reviewers to check your PR.

 - If your PR is good, the reviewer will merge it.

 - If not, then you will be asked to make changes. In that case do everything that's required and contact the reviewer again once changes has been made.



## PR messages

Things that you **MUST** include in your pull request message:
 - `#What` - a list of features and fixes that were made
 - `#How` - a concise description of how these changes were implemented

Things that you **SHOULD** include in your pull request message:
- `#Why` - reasons for implementing these changes, (this will make reviewers' lifes easier)
- `#Testing` - description of how testing was conducted.

**Sample PR**

```
# What

 - 5 new hand gestures
 - Fixed an issue with the mouse moving around when the hand is stationary
 
# How

 - Hand gestures: 
Trained a few models using video samples from here: (pretend there is a link here).
Updated the configuration view to include new gestures.

 - Mouse jiggling fix:
Added a small motion radius around each hand joint 
which diables mouse movement unless the joint goes outside the radius.

# Why

 - Hand gestures: Dean asked me

 - Mouse jiggling fix: 
It prevented featureX to work and it generally just annoyed the hell out of me.

# Testing

Used X framework for unit tests

Compiled the project and attempted evey gesture by myself and forced all fo my friends to do the same
```

# Code quality

**PLEASE** document your code. Reviewers will **NOT** merge your branch until its properly documented.

**PLEASE** Compile and test your code. Reviewers will **NOT** merge your branch until your code is compilable.
