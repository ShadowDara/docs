# samfile

[Back Home](#) - [Download Page](#/download) - [Search](#/search)

samfile is custom make inspired file by me (Shadowdara).


## copy paste samfile

```
# Lines starting with # are comments
// This is a comment too
-- and this too

build:
    ECHO Running the build
    RUN bun run build

```


## Task Naming

i would recommend the users to make task which does not start with `_` in general and no especially not with `_b`. The good thing you will see, every Task name. But i just want to recommend it.


## Commands

The samfile has a lot of commands which are available. Click [here](#/samfile/commands) to view a full list for every command.


## Install

Simply install the samfilerunner with and then run it via `seg`!


### cargo

```
cargo install samtool
```


### npm

```
npm i @shadowdara/seg
```


## Runners

This is an overview about the samfile runners and which commands they are supporting

*View the statistic [here](#/samfile/runners)*


### Download


### Ideas / TODO

- move samfile to the root dir instead of `.samengine` but both will work, but the .samengine directory will probably generated an info message that this is not neccessary anymore, but the support for it will not be removed!
- Add new field for a timer which be started and then stopped and printed to the command line
- *(I planning to make it slowly to an mix between shell and make)*


*EDIT DATE: 11.07.2026*
