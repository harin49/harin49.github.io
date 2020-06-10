---
layout: post
title:  "Downgrading brew packages manually?"
date:   2020-06-09 22:00:00 GMT+0530 
---

I recently had to install a downgraded version of a brew package - [react-native-debugger](https://github.com/jhen0409/react-native-debugger), but dang! [Homebrew](https://brew.sh/) did not have a separate formula for that specific version of react-native-debugger. I had to find a way to manually choose the required version available in homebrew and install it. I've enumerated the steps required below! 

## The Idea
Since homebrew based package installation are based on git and ruby, it's quite simple to achieve what we want! A package in homebrew is installed based on the formulae which in turn is chosen based on the commit SHA ids of each of the versions of the package if published by the author! you can find them [here!](https://github.com/Homebrew) Be sure to choose the right formulae! 

_Hint: 3rd party GUI applications in homebrew are stored/referred from the homebrew-cask and homebrew-core consists of binaries maintained by the homebrew team!_

Now, lets install the right version of react-native-debugger.

#### Step: 1

> Skip this step if you don't have an existing installation of the application already!

First let's remove the existing/incorrect version of react-native-debugger. 

`brew cask uninstall react-native-debugger`

#### Step: 2

Now we have to select the commmit SHA id of the verison we want to downgrade to! 

we can do this in two ways by either
* visiting the github repo for homebrew and navigating to the right tap and required packages' .rb file! and then take a look at the .rb file's history!
* or by using the homebrew tap locally on our machine! by executing the following command

`git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask log Casks/react-native-debugger.rb`

This command displays the commit logs for the required package and we can choose the commit id based on the required version! 

> note: change the above command to suit your package name and tap!

#### Step: 3

Choose the commit SHA id for the required version of the package from the git commit logs displayed by the command provided in step-2

In my case :
 commit SHA id: b6ac3795c1df9f97242481c0817b1165e3e6306a for the version 0.10.7 of react-native-debugger. 

once we have the required commit SHA id, execute the below command!

`git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask checkout b6ac3795c1df9f97242481c0817b1165e3e6306a Casks/react-native-debugger.rb`

> note: similar to note in step-2, change the above command to suit your package name, tap and commit SHA id!

#### Step: 4 

Okay, last step! We have basically asked home-brew to ignore the latest verison of the package formulae and instead use the version that is selected by the command in step-3! so go right ahead and install the package using brew commands!

In my case : 
`brew cask install react-native-debugger`

and that's it!

PS: I really liked using homebrew! neat little package manager and very easy to follow too!

