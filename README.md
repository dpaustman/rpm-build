# rpm-build
%define name sem_tool
%define version 1.0.0
%define release 1%{?dist}


Name:    %{name}
Summary: %{name}
Version: %{version}
Release: %{release}
Group:   HUAWEI
License: GPL

%description
sem tool for rpm

%install
mkdir -p ${RPM_BUILD_ROOT}/usr/sbin
mkdir -p ${RPM_BUILD_ROOT}/etc
cp %{_sourcedir}/sem_tool.sh ${RPM_BUILD_ROOT}/usr/sbin/sem_tool
cp %{_sourcedir}/*.properties ${RPM_BUILD_ROOT}/etc
chmod 755 ${RPM_BUILD_ROOT}/usr/sbin/sem_tool
chmod 640 ${RPM_BUILD_ROOT}/etc/*.properties

%files
%defattr(-,root,root,-)
/usr/sbin/sem_tool
/etc/timezones.properties


cd ~
mkdir rpmbuild/BUILD -p
mkdir rpmbuild/BUILDROOT -p
mkdir rpmbuild/RPMS -p
mkdir rpmbuild/SOURCES -p
mkdir rpmbuild/SPECS -p
mkdir rpmbuild/SRPMS -p

https://www.cnblogs.com/klb561/p/9189236.html  iso
https://blog.csdn.net/qq_42761569/article/details/104018903  python3 hbase
1、在tomcat/bin/shutdown.sh文件中增加一个参数

在文件最后一行的命令添加一个force exec "$PRGDIR"/"$EXECUTABLE" stop -force "$@"
2、在tomcat/bin/catalina.sh脚中，加入下面这三行

在这一行后面   PRGDIR=`dirname "$PRG"`

if [ -z "$CATALINA_PID" ]; then
    CATALINA_PID=$PRGDIR/CATALINA_PID
    cat $CATALINA_PID
fi

3、在tomcat/bin/下面新建setenv.sh文件，文件内容如下：

#!/bin/bash
CATALINA_PID=$CATALINA_HOME/bin/CATALINA_PID

-----------------------------------------------------------------------------------------------------

原因如下：

linux的线程是通过进程实现的。 2.6内核32位系统上 gcc -static编译出来的程序 会让多线程表现成多进程的状态，出现同名多个PID 不带-static就表现为只有一个PID 64位系统，不管加不加-static，都只有一个PID 感觉32位和64位在线程的实现不一样。
