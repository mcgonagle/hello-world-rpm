# Hello-World RPM spec file.
## Creating an RPM package can be complicated. Here is a complete, working RPM Spec file with several things skipped and simplified.
Directions copied from [here](https://rpm-packaging-guide.github.io/). 

```
Name:       hello-world
Version:    1
Release:    1
Summary:    The simplest hello world RPM package
License:    GPL-2.0
URL:        https://github.com/mcgonagle/hello-world-rpm
# Sets the build target to architecture-independent
BuildArch:      noarch


%description
This is my first RPM package, which does nothing.

%prep
# There is no source, so nothing here

%build
cat > hello-world.sh <<EOF
#!/bin/bash
echo Hello world
EOF

%install
mkdir -p %{buildroot}/usr/bin/
install -m 755 hello-world.sh %{buildroot}/usr/bin/hello-world.sh

%files
/usr/bin/hello-world.sh

%changelog
* Sun Sep 13 2026 Thomas A. McGonagle <mcgonagle@gmail.com> - 1.1
- Update to hello-world rpm spec file
```
Save this file as hello-world.spec.

Now use these commands:
```
$ rpmdev-setuptree
$ rpmbuild -ba hello-world.spec
```
