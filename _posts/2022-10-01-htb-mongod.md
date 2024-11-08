---
title: HTB Mongod
date: 2022-10-01 22:48:00 +0800
categories: [HTB]
tags: [Linux, Databases, MongoDB]
pin: false
author: GRX6
layout: post
---

## Reconnaissance/Intelligence Gathering

In this step we collect the target information available in public repositories or sources. We do everything passively.

## Scanning and enumeration

Now it's time to start the active scanning.

As always, we define our TARGET and hosts file of our machine to facilitate the process.

```console
TARGET=10.129.229.227
echo "10.129.73.196 mongod.htb" | sudo tee -a /etc/hosts
```

We launch a single `TCMP` probe to check ping.

```console
ping -c 1 $TARGET # => Ping is working
```

Ping is working and from the `ttl` we are able to see that it is a linux machine.

### NMAP

To scan the `target` to find open ports and possible vulnerabilities we use `nmap`.

First, simple `TCP` scan without `DNS` resolution and ping discovery, to all the ports and with the version detection.

```console
nmap -n -Pn -sV -p- $TARGET -vvv -oG allPorts
```

We find that the port `27017` is open, we will run the scripts to see what service is listening.

```console
nmap -n -Pn -sVC -p27017 $TARGET -vvv -oN targeted
```

The result show that it is a `MongoDB`. We will use `mongo cli` to see the contents of the database.

The flag is inside a collection.
