---
layout: simple
author_profile: false
permalink: /manual
classes: wide
title: Korsimoro Control KBASH Manual (kc command)
toc: true
---

# kc

```shell
kc [COMMAND] [help|--help|-help|-h|?] ...

kc is a bash environment supporting development.

Functions (modify the current shell)
 activate                   Configure shell to match build environment for [COMPONENT]
 add-command                Add a command to the kc environment.
 add-component              Add a new component (command scope and directory pair)
 add-function               Add a function.
 build                      Build [C] using component build system
 bundle                     Runs the project specific bundle
 cd                         cd /home/korsimoro/K/[PATH] (or base w/o arg)
 clean                      Remove as many artifacts for [C] as we know about
 deactivate                 Restores key variables to boot state
 describe                   Describe information about this build env
 kbash-env                  Display current environment settings.
 kbash-os                   Display os
 kbash-troff                disable KBASH_TRACE
 kbash-tron                 set KBASH_TRACE to trace KBASH internals
 parallel                   Control how many jobs run in parallel.
 reset                      Reload the environment.
 setup                      Initialize a development environment
 troff                      Stop bash execution trace.
 tron                       Start bash execution trace.


Commands (run as subprocesses)
 about                      Detailed Information about KBASH
 component-list             List all available components
 klang                      Manage KBASH top level languages
 manual                     Generate help manual

Components
 devops                     Description of devops
 docs                       Description of docs

Use kc [FUNCTION|COMMAND|COMPONENT] help for more information.
```

## Functions

Functions manipulate the local shell variables, unlike commands, which are
executed by the shell as a subprocess.

### ```activate```

kc activate [help|--help|-help|-h|?] [COMPONENT]

Configure shell to match build environment for [COMPONENT]



### ```add-command```

kc add_command [help|--help|-help|-h|?] COMMAND_NAME

Add a command to the kc environment.

This will create the file
  /home/korsimoro/K/kbash/commands/[COMMAND_NAME].sh
if it does not exist.  You should then edit this file to implement.
The template file used in creation is located at
  /home/korsimoro/K/.kbash/setup/command.sh
You will want to edit 3 things
 1. The oneline help summary that is used in other contexts
 2. The print_help() function, which is the detailed help
 3. The run() function, which is executed as a subprocess



### ```add-component```

kc add_component [help|--help|-help|-h|?] [COMPONENT_ID] [KC]

Add a new component (command scope and directory pair)


usage: add-component [COMPONENT_ID] [KC]

This will set up a component in the directory
 - /[COMPONENT_ID]
and will create
  .... more info

A component



### ```add-function```

kc add_function [help|--help|-help|-h|?] FUNCTION_NAME

Add a function.

This will create the file
  /home/korsimoro/K/kbash/functions/[FUNCTION_NAME].sh
if it does not exist.  You should then edit this file to implement.
The template file used in creation is located at
  /home/korsimoro/K/.kbash/setup/function.sh
You will want to edit the 4 function stubs
 1. oneline_help_kc_[FUNCTION_NAME]
 2. cmdline_help_kc_[FUNCTION_NAME]
 3. help_kc_[FUNCTION_NAME]
 4. run_kc_[FUNCTION_NAME]



### ```build```

kc build [help|--help|-help|-h|?] [COMPONENT]

Build [C] using component build system



### ```bundle```

kc bundle [help|--help|-help|-h|?] [Bundle Commend Line]

Runs the project specific bundle


This runs the correctly scoped bundle - ruby requires
a complete path to the bundle wrapper in order to
set the environment correctly.



### ```cd```

kc cd [help|--help|-help|-h|?] [PATH]

cd /home/korsimoro/K/[PATH] (or base w/o arg)

This is a shell function, which execute cd as follows:
  cd /home/korsimoro/K/[PATH].

If no PATH is provided, this just cds into
  cd /home/korsimoro/K



### ```clean```

kc clean [help|--help|-help|-h|?] [COMPONENT]

Remove as many artifacts for [C] as we know about

kc clean [COMPONENT] ...

  Goal : Remove as many artifacts for [C] as we know about

Components
 devops                     Description of devops
 docs                       Description of docs



### ```deactivate```

kc deactivate [help|--help|-help|-h|?]

Restores key variables to boot state



### ```describe```

kc describe [help|--help|-help|-h|?] [COMPONENT]

Describe information about this build env

kc describe [COMPONENT] ...

  Goal : Describe information about this build env

Components
 devops                     Description of devops
 docs                       Description of docs



### ```kbash-env```

kc kbash_env [help|--help|-help|-h|?]

Display current environment settings.

kc env



### ```kbash-os```

kc kbash_os [help|--help|-help|-h|?]

Display os

This command will report what the kbash utilities think the current operating
system is.

You can use the following functions in the shell environment (or your own)
scripts, if you want a quick check to determine your operating system
- is_osx
- is_linux
- is_windows

This is based off of ```uname``` - so.  You can use kbash-os to show you
the uname output and check the value so is_osx, is_linux, is_windows

For example:
```shell

  > kc kbash-os
  Checking os: uname ='Linux kisia 4.15.0-48-generic #51-Ubuntu SMP Wed Apr 3 08:28:49 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux'
  Linux Detected
  >
```



### ```kbash-troff```

kc kbash_troff [help|--help|-help|-h|?]

disable KBASH_TRACE

This is equivalent to
  export KBASH_TRACE=false



### ```kbash-tron```

kc kbash_tron [help|--help|-help|-h|?]

set KBASH_TRACE to trace KBASH internals

This is equivalent to
  export KBASH_TRACE=true



### ```parallel```

kc parallel [help|--help|-help|-h|?] MAXJOBS

Control how many jobs run in parallel.


Control how many jobs run in parallel



### ```reset```

kc reset [help|--help|-help|-h|?]

Reload the environment.

In this shell, execute:
  /home/korsimoro/K/activate.sh

This will cause the entire kc runtime to be reloaded,
so any changes to functions or commands will be processed.

This will update the activation count from 0 to 1



### ```setup```

kc setup [help|--help|-help|-h|?] [COMPONENT]

Initialize a development environment



### ```troff```

kc troff [help|--help|-help|-h|?]

Stop bash execution trace.

Equivalent to
  set +x



### ```tron```

kc tron [help|--help|-help|-h|?]

Start bash execution trace.

Equivalent to
  set -x



5
## Commands

### ```about```

```shell
kc <command> [help]

kc is a bash environment supporting development.

kc is pure anti-pattern, in includes
 - 'within-environment' mutations- bash functions allow forward mutation of the
   active environment, with no guarantees of any stable state, save the single
   application of this function after a clean reset
 - pure 'side-effect' focus.  This is an attempt to identify mutators to the
   filesystem, and to codify them.  All functions and commands in the
   environment are expected to operate upon the filesystem directly.  git
   provides us exceptional visiblity into changes over the active checkout.

kc supports the development of ad-hoc tasks required
to effectively build a complex, multi-project system.

As knowledge is captured w/in the kc script system, it is added
into the compiled node or python build support tools.  But when you have to
adapt to an existing culture, as in a fork, you need a little grease.  The
node and python knowledge is the organized grease to glue a complete system
onto a consistent base.

kc uses a "Convention over Configuration" and heavily seeds a
bash operating environment with functions and variables, supporting
multi-tech integration projects.  The ability to "regenerate" the environment
from the kc reset command means that scripts can be rapidly
edited and applied - recorded in a pull-request, and the collective wisdom
knitting forward.

kc can be rapidly and ad-hoc adjusted, and it is specific to
this repository.  The bashenv orchestrates the connection of the environment
with a conversational mutator - a live bash shell.  As this is bound to a
repository top, the space underneath is managed - so this is effectively a
bash shell over a commit-trail of reference.

kc is scoped by directory (or checkout) - based on the KC
variable.
  KC = /home/korsimoro/K

For more information, check out this file:
/home/korsimoro/K/docs/bashenv.md

In general use kc [cmd] help for more information.
```

### ```component-list```

```shell
Show component list
```

### ```klang```

```shell
kc klang kc [LANG] ....

Manage languages

Commands (run as subprocesses)
 node                       System Node
 python                     Manage python configuration
 ruby                       System Node
```

#### ```node```

```shell
kc klang/node kc node [LANG] ....

Manage Local Node
```

#### ```python```

```shell
kc klang/python kc klang python [LANG] ....

inspect the local python environment

Commands (run as subprocesses)
 info                       System python information
```

##### ```info```

```shell
Command not found - no 'info help' in 'project/klang/python'
```

#### ```ruby```

```shell
kc klang/ruby kc ruby [LANG] ....

Manage Local Ruby

Commands (run as subprocesses)
 cleanrvm                   Detailed Information about KBASH
 info                       Where
 installrvm                 Detailed Information about KBASH
 resetrvm                   Detailed Information about KBASH
```

##### ```cleanrvm```

```shell
Command not found - no 'cleanrvm help' in 'project/klang/ruby'
```

##### ```info```

```shell
Command not found - no 'info help' in 'project/klang/ruby'
```

##### ```installrvm```

```shell
Command not found - no 'installrvm help' in 'project/klang/ruby'
```

##### ```resetrvm```

```shell
Command not found - no 'resetrvm help' in 'project/klang/ruby'
```

### ```manual```

```shell
Recursively assemble documentation as a markdown
file.
```


## Components

|Component|Description|
|-|-|
|devops|Description of devops|
|docs|Description of docs|


### ```devops```

```shell

kc devops <<DESCRIBE ANY OPTIONS FOR THIS SCOPE>>


kc devops commands

Commands (run as subprocesses)
 info                       view docs
 update-compose             view docs
```


#### ```info```

```shell
kc devops info

Info about kc devops
```

#### ```update-compose```

```shell
kc devops update-compose [TARGET]

Info about kc devops
```

### ```docs```

```shell

kc docs <<DESCRIBE ANY OPTIONS FOR THIS SCOPE>>


kc docs commands

Commands (run as subprocesses)
 info                       view docs
 serve                      view docs
```


#### ```info```

```shell
kc docs info

Info about kc docs
```

#### ```serve```

```shell
kc docs serve

Run bundle serve
```


## About

```shell
kc <command> [help]

kc is a bash environment supporting development.

kc is pure anti-pattern, in includes
 - 'within-environment' mutations- bash functions allow forward mutation of the
   active environment, with no guarantees of any stable state, save the single
   application of this function after a clean reset
 - pure 'side-effect' focus.  This is an attempt to identify mutators to the
   filesystem, and to codify them.  All functions and commands in the
   environment are expected to operate upon the filesystem directly.  git
   provides us exceptional visiblity into changes over the active checkout.

kc supports the development of ad-hoc tasks required
to effectively build a complex, multi-project system.

As knowledge is captured w/in the kc script system, it is added
into the compiled node or python build support tools.  But when you have to
adapt to an existing culture, as in a fork, you need a little grease.  The
node and python knowledge is the organized grease to glue a complete system
onto a consistent base.

kc uses a "Convention over Configuration" and heavily seeds a
bash operating environment with functions and variables, supporting
multi-tech integration projects.  The ability to "regenerate" the environment
from the kc reset command means that scripts can be rapidly
edited and applied - recorded in a pull-request, and the collective wisdom
knitting forward.

kc can be rapidly and ad-hoc adjusted, and it is specific to
this repository.  The bashenv orchestrates the connection of the environment
with a conversational mutator - a live bash shell.  As this is bound to a
repository top, the space underneath is managed - so this is effectively a
bash shell over a commit-trail of reference.

kc is scoped by directory (or checkout) - based on the KC
variable.
  KC = /home/korsimoro/K

For more information, check out this file:
/home/korsimoro/K/docs/bashenv.md

In general use kc [cmd] help for more information.
```
