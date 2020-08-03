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
