#
#  Author: Hari Sekhon
#  Date: 2016-01-16 09:58:07 +0000 (Sat, 16 Jan 2016)
#
#  vim:ts=4:sts=4:sw=4:et
#
#  https://github.com/harisekhon/Dockerfiles
#
#  If you're using my code you're welcome to connect with me on LinkedIn and optionally send me feedback to help improve or steer this or other code I publish
#
#  https://www.linkedin.com/in/harisekhon
#

# Alpine's underlying libraries are causing find_active_server.py --https mode to run all threads concurrently without respecting the --num causing indeterministic results and failing tests/test_find_active_server.sh
FROM harisekhon/pytools:centos
MAINTAINER Hari Sekhon (https://www.linkedin.com/in/harisekhon)

LABEL Description="DevOps Tools (CentOS)"

ADD build.sh /

WORKDIR /github

RUN /build.sh

ENV PATH $PATH:/github/pytools:/github/bash-tools:/github/perl-tools

# trying to do -exec basename {} \; results in only the jython files being printed
CMD ["/bin/bash", "-c", "find /github -maxdepth 2 -type f -iname '[A-Za-z]*.py' -o -iname '[A-Za-z]*.jy' -o -iname '[A-Za-z]*.sh' -o -iname '[A-Za-z]*.pl' | xargs -n1 basename | sort"]