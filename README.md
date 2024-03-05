# Hello-World RPM spec file.
## Creating an RPM package can be complicated. Here is a complete, working RPM Spec file with several things skipped and simplified.
Directions copied from [here](https://rpm-packaging-guide.github.io/). 

```
Name:       hello-world
Version:    1
Release:    1
Summary:    Most simple hello-world RPM package
License:    Apache 2.0

%description
This is my first RPM package, which does nothing.

%prep
# we have no source, so nothing here

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
# let's skip this for now
```
Save this file as hello-world.spec.

Now use these commands:
```
$ rpmdev-setuptree
$ rpmbuild -ba hello-world.spec
```
