---
layout: post
title:  "What did I do with my old router?"
date:   2020-05-17 23:54:00 GMT+0530 
---
Before we dig into the post! I just want to give myself a pat for finally sitting down to write blogs! I've been deliberating about this for quite some time now. Hopefully, I'll continue this practice on a regular basis!

At long last I replaced my old router a couple of weeks back to get better coverage, bandwidth and was wondering what I'd do with my existing router. After spending some time on google I decided to use the older router as an wireless access point in combination with my new router to extend the range of my Wi-Fi. Down below, I have listed the steps I followed.

## The Idea
The simple idea is to re-use old/extra routers as wireless access points for your network. 

> * All we need for this is an extra router (obviously), an extra ethernet cable and some time!
> * We'll be addressing the new router as Router-A and the surplus router as Router-B
> * If Router-B has an access point mode, save yourself some hassle and enable the access point mode and jump directly to step-5! (_This sure makes life easy!_)

#### Step: 1

> Now, if you want to avoid setting up a static IP address for Router-B. You can skip step 1 & 2 and directly go over to step 3.

The first step is to make sure that you have an existing/working network connection set-up with Router-A. Once connected, login to the router configuration page through your browser. This is usually done by entering the default router address on your browser's URL search bar. The common router addressess used by major router brands are listed below. 

* 192.168.1.1
* 192.168.0.1
* 10.0.0.1
* 10.0.1.1

If your router is a netgear router then go ahead and login using www.routerlogin.net. Still not able to login to your router settings? just google it.

Now, login to the page by using the required credentials.

#### Step: 2
Navigate to the LAN settings, once you're logged in to the router's configuration page. We need to reserve an [IP address](https://en.wikipedia.org/wiki/IP_address) from Router-A's network to be used as the static IP address for Router-B. This is highly recommended so as to avoid IP conflicts, dynamic addresses being assigned to router-B on every connection reset.

Choose an IP address from Router-A's network address range and reserve it for Router-B by manually binding the chosen IP address with Router-B's MAC address.

> * [MAC address](https://en.wikipedia.org/wiki/MAC_address) for the router can be found under the it.
> * Make sure you choose an IP address that is within the range of Router-A's network addresses.
> * Be sure to note down the static IP address as we'll make use of it in later steps.

#### Step: 3
Connect the ISP(internet service provider)/Internet cable to the [WAN](https://en.wikipedia.org/wiki/Wide_area_network) port of Router-B and follow instructions from step 1 to login to Router-B's configuration page.

#### Step: 4
The thought behind this step is to configure Router-B to work as just an access point, forwarding requests to Router-A rather than work as a router itself and try to access the internet. This can be done by disabling the [DHCP](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol) option in the Router-B's settings and assigning an static IP address. This basically stops Router-B from assigning IP addresses to devices that could be connected to itself. 

_Follow the below instruction only if you had decided to create a static IP address._  
Under [LAN](https://en.wikipedia.org/wiki/Local_area_network) setup again, enter the static IP address we had made a note of earlier on the IP address input box.

 Apply/Save the settings!

#### Step: 5
Okay! the final step. Remove the ISP(internet service provider)/Internet cable from Router-B's WAN port and connect it to Router-A's WAN port. Use the ethernet cable to connect Router-A's LAN port with Router-B's LAN port and it's done!

![example router network architecture](/assets/extra_access_point.png)

Let me know what you guys think about this over [here](https://twitter.com/harithegooner)! 
