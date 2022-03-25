# PiCode Install Docker Action

Install docker and docker-compose with ease.

_Note: This is meant to be used on an Ubuntu machine version 20.04.03 or newer._

## Usage

```yml
- uses: picodebr/install-docker-action@v1.1
  with:
    # remote server private ssh key (required)
    ssh_key: ""

    # remote server username (required)
    ssh_user: ""

    # remote server address (required)
    ssh_host: ""

    # time in seconds needed for the remote machine to completely reboot (default 60s)
    reboot_time: ""
```

## Example

The following example shows how install docker and docker-compose in the remote machine
everytime something is pushed onto the master branch.

```yml
name: Install docker and docker-compose

on:
  push:
    branches: [master]

jobs:
  main:
    runs-on: ubuntu-latest
    steps:
      - name: List remote home directory
        uses: picodebr/install-docker-action@v1.1
        with:
          ssh_key: ${{ secrets.SSH_KEY }}
          ssh_user: ${{ secrets.SSH_USER }}
          ssh_host: ${{ secrets.SSH_HOST }}
          reboot_time: 120 # 120 seconds = 2 minutes
```
