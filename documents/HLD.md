## Introduction
This document serves as an overview of the IT Security project, which consists of picking and
creating a working solution to a given part of a system. The group decided to take on implementing
a system for control administrative privileges and locking down ports, protocol and services in the
network.

The scope of the project is within the testing real of the pre-exsiting network from the Network
Project. After the testing has passed successfully an implementation within the working
CHINANET would be possible. This might also be used within other cases which will be expanded
on in the process of the work.

The purpose is to learn and have a working example of a “fortified” management system within a
heavily used and open to attacks network.

The goal is to have this security point implemented and is reproducible in a number of situation
where this is useful.

The customer in this case is the lecturer who is managing the CHINANET system and all final
decisions are outside the team's reach.

Key persons for this project are as follow: Team members, Lecturer and Classmates.

## Overview
In this section, there will be a technical explanation and overview of the testing network.

On the following illustration the primary use cases of this system will be depicted.
As this is a system used only for testing purposes, these use cases will change once they are to be
implemented in the “live” system.

![Use Case](https://github.com/lydiavasileva/hard-lockdown/blob/master/documents/diagrams/Use%20Case%20Diagram.png)

Illustration 1: Use Case Diagram

There will be a diagram explaining how the devices will be connected.

![Network Diagram](https://github.com/lydiavasileva/hard-lockdown/blob/master/documents/diagrams/Virtual%20Diagram.png)

The diagram shows the entire network, which in this stage is small and simple. There is a Juniper
security device named vSRX, with two connected networks. The management network is only for
managing the router, from a local host. Since it will be preferable to access the router from the
outside, there is a Jump-host which will be reachable from the outside. To access the man-host the
user will have to SSH to the JH first.

The other network will be for normal users, where they will connect their personal devices. Since
we do not have access to the devices, the vSRX will be configured with certain services allowed.

## Performance
Since it is still a small network, the performance will not be a concern. Depending on the number of
users using the USR network, there might be a need for a faster Internet connection in the future.

## Security and privacy
The management network will be heavily secured, so only specific credentials will be able to log on
the system. Since we do not want the man-host to be accessible from the outside, there will be an
SSH JH. It will only be this device, which will be reachable from the outside. This will ensure only
users with the allowed credentials, can log on the system and configure the router.
The USR network will also be secured, so no illegal services can access the Internet. Since we do
not have access to the devices, all the security configurations will be done on the vSRX.

## Hardware
All the devices will be virtual devices in VM Ware, which will be running on a single physical host.
Linux distribution for the hosts
Juniper SRX for the router

## Protocols and standards
- [SSH](https://en.wikipedia.org/wiki/Secure_Shell) – Secure Shell
SSH is used for secure connections, it is normally used on top of TCP or IP and for login
Authentication on a remote access, or to communicate on an insecure network.
SSH will be used on the server for the login.

- [802.3](https://en.wikipedia.org/wiki/IEEE_802.3) – IEEE 802.3 ETHERNET
The standard for Ethernet networks.


## IP layout
This layout may be changed during the course of work.

Management Network

Net ID: 10.10.10.0/29

SM: 255.255.255.248

GW: 10.10.10.1

JH: 10.10.10.2

man-host: 10.10.10.3

## Naming convention
Virtual Router – vSRX

Jump Hosts – JH

Management Linux Box – man-host

User Hosts (XX number of host) – host_XX
