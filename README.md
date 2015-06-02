# jprops2bash

Convert Java properties file to bash env var script

## Usage

It reads from stdin and writes to stdout:

    $ cat > sample.properties
    teamcity.agent.jvm.file.encoding=UTF-8
    teamcity.agent.jvm.file.separator=/
    teamcity.agent.jvm.os.arch=amd64
    teamcity.agent.jvm.os.name=Linux
    teamcity.agent.jvm.os.version=3.13.0-43-generic
    teamcity.agent.jvm.path.separator=\:
    teamcity.agent.jvm.specification=1.8
    teamcity.agent.jvm.user.country=US
    teamcity.agent.jvm.user.home=/home/teamcity
    runParam.script.content=\#\!/bin/bash\n\nset -o errexit\n\# set -o xtrace\n\necho "*** <Root project> \:\: \\"run pipeline script\\"

    $ jprops2bash < sample.properties
    TEAMCITY_AGENT_JVM_FILE_ENCODING='UTF-8'
    TEAMCITY_AGENT_JVM_FILE_SEPARATOR='/'
    TEAMCITY_AGENT_JVM_OS_ARCH='amd64'
    TEAMCITY_AGENT_JVM_OS_NAME='Linux'
    TEAMCITY_AGENT_JVM_OS_VERSION='3.13.0-43-generic'
    TEAMCITY_AGENT_JVM_PATH_SEPARATOR=':'
    TEAMCITY_AGENT_JVM_SPECIFICATION='1.8'
    TEAMCITY_AGENT_JVM_USER_COUNTRY='US'
    TEAMCITY_AGENT_JVM_USER_HOME='/home/teamcity'
    RUNPARAM_SCRIPT_CONTENT='#!/bin/bash\n\nset -o errexit\n# set -o xtrace\n\necho "*** <Root project> :: \"run pipeline script\"'
