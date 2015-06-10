FROM ubuntu:14.04
MAINTAINER Luigi Ballabio <luigi.ballabio@gmail.com>
LABEL Description="Provide a building environment where the Boost C++ libraries are available"

ENV major=1 minor=57 patch=0

RUN apt-get update && apt-get install -y build-essential wget
RUN wget http://downloads.sourceforge.net/project/boost/boost/${major}.${minor}.${patch}/boost_${major}_${minor}_${patch}.tar.gz \
    && tar xfz boost_${major}_${minor}_${patch}.tar.gz \
    && rm boost_${major}_${minor}_${patch}.tar.gz
RUN cd boost_${major}_${minor}_${patch} \
    && ./bootstrap.sh \
    && (./b2 --prefix=/usr install || true) \
    && cd .. && rm -rf boost_${major}_${minor}_${patch} && ldconfig
