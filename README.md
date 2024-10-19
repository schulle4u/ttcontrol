<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a></p>

# TTControl
Controls multiple server instances of the TeamTalk voice conferencing software.

## Introduction

Since there are only a few tools available for managing multiple TeamTalk servers on one system, I provide my own script here. This shell script provides functions to control one or more TeamTalk server instances. The usual commands for starting, restarting, stopping and querying the status are provided. In addition, the directory structure for a new server can be created and passed to the setup wizard. The final setup assumes that each server runs in its own working directory. 

## Setup

1. Download and install the latest [TeamTalk server binary](https://bearware.dk). 
2. Create a home directory to store your server configurations (e.g. `mkdir -p /var/lib/teamtalk/servers`). 
3. Clone this repository or [download](https://github.com/schulle4u/ttcontrol/archive/refs/heads/main.zip) to a desired directory.
4. If needed, customize the `Configuration` section of the `ttcontrol` file.
  * `tt_bin` = path to the TeamTalk server binary file (default: `/usr/local/bin/tt5srv`).
  * server_dir` = path to the main directory for the server configurations; the subdirectories are created here (default: `/var/lib/teamtalk/servers`, must be created correctly before).
  * `tt_user` = user under which the TeamTalk servers should run (default: `teamtalk`, must be set up correctly before).
5. If not already done, create a new server: `sudo ./ttcontrol create server_name`.
6. Start all servers: `sudo ./ttcontrol start`.

## Syntax
`sudo ./ttcontrol {clean|create|start|stop|restart|status} {server_name}`.

The following commands are supported: 

* `clean {servername}`: Clean all or specific servers from abandoned files.
* `create {servername}`: Create a new server, server name is mandatory.
* start {servername}: Start all or specific servers.
* stop {servername}: Stop all or specific servers.
* restart {servername}: Restarts all or specific servers.
* status {servername}: Get the running status of all or specific servers.

## Development
Copyright (C) 2024 Steffen Schultz, released under the terms of the MIT license: This software is not associated with TeamTalk or other products developed by BearWare.dk. Use at your own risk!