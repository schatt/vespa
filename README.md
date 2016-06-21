# Vespa

Vespa is an engine for low-latency computation over large data sets.
It stores and indexes your data such that queries, selection and processing over the
data can be performed at serving time.

This README describes how to build and develop the Vespa engine.
For user documentation see TODO: Github pages link

## Getting started developing

### Setting up local git config

    git config --global user.name "John Doe"
    git config --global user.email johndoe@host.com


### Setting up build environment

C++ building is currently supported on CentOS 7.

#### Install required build dependencies

    sudo yum -y install epel-release centos-release-scl
    sudo yum-config-manager --add-repo https://copr.fedorainfracloud.org/coprs/g/vespa/vespa/repo/epel-7/group_vespa-vespa-epel-7.repo
    sudo yum -y install RUN yum -y install devtoolset-4-gcc-c++ devtoolset-4-libatomic-devel \
        Judy-devel cmake3 ccache lz4-devel zlib-devel maven libicu-devel llvm-devel \
        llvm-static java-1.8.0-openjdk-devel openssl-devel rpm-build make \
        vespa-boost-devel vespa-libtorrent-devel vespa-zookeeper-c-client-devel vespa-cppunit-devel

or use our prebuilt docker image

    # TODO: Add docker command

### Building Java modules

Java modules can be built on any environment having Java and Maven:

    sh bootstrap.sh
    mvn install

### Building C++ modules

    source /opt/rh/devtoolset-4/enable
    sh bootstrap.sh
    mvn install -DskipTests -Dmaven.javadoc.skip=true
    cmake .
    make
    make test

### Create RPM packages

    sh dist.sh VERSION && rpmbuild -ba ~/rpmbuild/SPECS/vespa-VERSION.spec

## Running Vespa on a local machine

* OS X : See [node-admin/README_MAC.md](node-admin/README_MAC.md)
* Linux : See [node-admin/README_LINUX.md](node-admin/README_LINUX.md)


Code licensed under the Apache 2.0 license. See LICENSE file for terms.

## Documenting your features

See [README-documentation.md](README-documentation.md).
