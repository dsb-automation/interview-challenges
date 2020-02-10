# Automation Engineer Challenge

**Expected task time:** 1-2 hours

## Intro

As can be inferred from our [RPA developer
challenge](../rpa-developer/ChallengeInstructions.md), we use Robotics Process
Automation (RPA) as a part of our automation toolchain at DSB. For the most
part, this makes sense, as DSB uses legacy systems that are often times
extremely costly to update or add APIs to. In this way, RPA allows the
department to automate processes that otherwise would be completed manually by a
person, and not a machine.

As can also be inferred from the RPA dev challenge, we use
[UiPath](https://www.uipath.com/) for our RPA tasks. While UiPath has created a
number of solutions, there is not an out-of-the-box platform solution that we
can simply plug into and play to start doing robot development. This means that
we must roll some of our own solutions when it comes to our robot coding setup.
This is where the automation engineer's role enters the picture. It is the
automation engineer that faces many tasks related to building the guardrails for
our developers. Whether it is an internal tool or a specific infrastructure, the
developers will use it and just care that it "works"--they don't care how.

## UiPath Robot Code Deployment

[UiPath Studio](https://docs.uipath.com/studio) (the program used to coding
robotics workflows) "outputs" `xaml` that are then packaged into NuGet packages.
The packaging from `xaml` files to NuGet packages is done by an executable that
comes in the UiPath Studio installation. When a process is ready to test or run,
the NuGet package is sent up to a web app called
[Orchestrator](https://docs.uipath.com/orchestrator) (also from UiPath), and the
web app uses the corresponding NuGet package to run a process.

The simplest way to do this "deployment" (`xaml` files -> built NuGet packages
-> pushed to Orchestrator) is what amounts to basically a [right-click
publish](https://damianbrady.com.au/2018/02/01/friends-dont-let-friends-right-click-publish/)
from UiPath Studio, where the `xaml` files are compiled, packaged, and pushed to
the Orchestrator web app that the user's machine is connected to.

## Your Challenge

This is where the challenge enters. Imagine that you have been employed at DSB.
You have learned that the robot developers are developing their code, and when
it comes time to push their changes into production, they do a right-click
publish from UiPath Studio up to UiPath Orchestrator, from which they then
update processes with the latest version. The team has previously tried to use a
version control system, but it was too cumbersome to learn and use--and just to
easy to do a deployment from UiPath Studio instead. The team also has varying
opinions of version control, and none of the team members have professional
experience with it.

Your challenge question is this:

```
Using a more modern day DevOps approach, how would you go about improving the process of deploying the robot code NuGet packages to Orchestrator?
```

## Provided Toolkit

You can assume you have the following at your disposal to use in the deployment
process redesign:

1. You have a stable UiPath Orchestrator where the robot code packages need to
   be pushed to, at some point in the CI/CD process
2. You have a platform to save code in version control
3. You have a standard CI/CD platform to run builds and deployments
4. You have an agent in from the CI/CD platform with the UiPath executable that
   can build NuGet packages from `xaml` files installed

## Required Tasks

Your tasks include:

1. Write a list of initial questions/thoughts that you have about the current
   process that you would inquire the developers and any other team members
   about before embarking on the process.
2. Prepare a 5-10 minute run-through of the new deployment process overview that
   you would propose to the team.
3. Describe how you would build buy-in from the RPA developers for you process
   and how you would account for varying levels in modern development standards.

## Bonus

If you were able to complete the first tasks in the alloted time, you can begin
working on these bonus questions:

1. How would you begin the process of code review for the robot code to be used
   in RPA processes?
2. How would you ensure a short build time on the build and deployment of the
   robot code?
3. Explain how you might design a process for testing the robot code NuGet
   packages and electing packages between different environments based on their
   (non)success.
