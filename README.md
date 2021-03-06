# sawsh
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FNoUseFreak%2Fsawsh.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2FNoUseFreak%2Fsawsh?ref=badge_shield)


SSH wrapper for aws to make your life easier.

## Features

 - Lookup AWS EC2 instances by name.
 - Lookup ip by `ip-xxx.xxx.xxx.xxx` format.
 - Transparant connect to ip

## Usage

```sh
$ sawsh webserver
```

This example will query AWS for a EC2 instance containing the name `webserver`. It will prompt you with a choise when
more than one result is found.

```sh
$ sawsh webserver
listing instances with tag core in: us-east-1
+---+--------------------+-------------+
|   |       NAME         |      IP     |
+---+--------------------+-------------+
| 0 | prod-webserver-1   | 10.1.1.10   |
| 1 | prod-webserver-2   | 10.1.2.10   |
| 2 | prod-webserver-3   | 10.1.3.10   |
| 3 | prod-webserver-4   | 10.1.1.11   |
| 4 | prod-webserver-5   | 10.1.2.11   |
| 5 | prod-webserver-6   | 10.1.3.11   |
+---+--------------------+-------------+
Pick a number: 1
Connecting to 10.1.2.10 ...
```

```
$ sawsh -h
NAME:
   sawsh - Query and connect to ec2 instances

USAGE:
   sawsh [global options] command [command options] [filter]

COMMANDS:
     list     Render a list of instances
     connect  Search and connect to an instance
     help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --help, -h  show help

COPYRIGHT:
   (c) Dries De Peuter <dries@depeuter.io>
```

## Install

### Official release

Download the latest [release](https://github.com/NoUseFreak/sawsh/releases).

```sh
$ wget https://github.com/NoUseFreak/sawsh/releases/download/0.1.0/darwin_amd64.tar.gz  -O - | tar -xz
$ sudo mv ./sawsh /usr/local/bin/sawsh
```

### Build from source

```sh
$ git clone https://github.com/NoUseFreak/sawsh.git
$ cd sawsh
$ make
$ make install
```

### Upgrade

To upgrade to the latest repeat the install step.

## Configure

Setup sure your [aws-cli](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html) is setup. That user needs `ec2:Describe*` permissions.

### Suggestion

It may be useful to setup some aliases if you use multiple aws accounts or want it to run with a non standard profile. 

```sh
$ alias prod_ssh='AWS_PROFILE=prod sawsh'
```


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FNoUseFreak%2Fsawsh.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FNoUseFreak%2Fsawsh?ref=badge_large)