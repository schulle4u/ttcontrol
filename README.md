<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a></p>

# TTControl
Controls multiple server instances of the TeamTalk voice conferencing software.

## Introduction

Since there are only a few tools available for managing multiple TeamTalk servers on one system, I decieded to provide my own script here. This shell script offers functions to control one or more TeamTalk server instances. The usual commands for starting, restarting, stopping and querying the status are included. In addition, the directory structure for a new server can be created and passed to the setup wizard. The final setup assumes that each server runs in its own working directory. 

## Recommended setup

1. Download and install the latest [TeamTalk server binary](https://bearware.dk). 
2. Create a system user under which the TeamTalk servers should run: `sudo adduser --system --group teamtalk`
3. Create a home directory to store your server configurations (e.g. `sudo mkdir -p /var/lib/teamtalk/servers`). 
4. Set permissions and ownership for your servers directory: `sudo chmod -R 774 /var/lib/teamtalk && sudo chown -R teamtalk:teamtalk /var/lib/teamtalk`
5. Clone this repository or [download](https://github.com/schulle4u/ttcontrol/archive/refs/heads/main.zip) to a desired directory.
6. If needed, customize the `Configuration` section of the `ttcontrol` file.
7. If not already done, create a new server: `sudo ./ttcontrol create server_name`.
8. Start all servers: `sudo ./ttcontrol start`.

## Configuration

The following options are available: 

* `tt_bin` = path to the TeamTalk server binary file (default: `/usr/local/bin/tt5srv`).
* `server_dir` = path to the main directory for the server configurations; the subdirectories are created here (default: `/var/lib/teamtalk/servers`).
* `tt_user` = user under which the TeamTalk servers should run (default: `teamtalk`).

## Syntax
`sudo ./ttcontrol {start|stop|restart|status|create|clean} {server_name}`

The following commands are supported: 

* `start {server_name}`: Start all or specific servers.
* `stop {server_name}`: Stop all or specific servers.
* `restart {server_name}`: Restarts all or specific servers.
* `status {server_name}`: Get the running status of all or specific servers.
* `create {server_name}`: Create a new server, server name is mandatory.
* `clean {server_name}`: Clean all or specific servers from abandoned files.

## Development
Copyright (C) 2024 Steffen Schultz, released under the terms of the MIT license: This software is not associated with TeamTalk or other products developed by BearWare.dk. Use at your own risk!