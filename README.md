# wsl-transdebian
A repository for WSL-only apt packages.

This includes packages for multiple distributions which use apt packages, not merely Debian. Currently supported are:

 * Debian 10 _buster_
 * Debian 11 _bullseye_
 * Debian 12 _bookworm_
 * Debian (testing) _sid_
 * Ubuntu _focal_
 * Ubuntu _bionic_
 
Deprecated (no longer updated) distributions include:

 * Debian 9 _stretch_

Please note that this list of currently supported distributions reflects only those which I have tested myself and as such am prepared to support. I don't have time to test against all other possibilities. This is not, of course, to say that any package posted here won't work on unlisted Ubuntu distributions or other Debian derivatives; merely that not having tested it myself, I'm not going to advertise that it _does_ by shipping a package entailed to that distribution. You will need to manually adjust the created `sources.list` file to use the most compatible distribution.

## Prerequisite

Make sure you have lsb_release installed

As root (`sudo -s`), enter the following commands:
```
apt install lsb_release
```

## Configuring the wsl-transdebian repo

As root (`sudo -s`), enter the following commands:

```ShellSession
wget -O /etc/apt/trusted.gpg.d/wsl-transdebian.gpg https://arkane-systems.github.io/wsl-transdebian/apt/wsl-transdebian.gpg

chmod a+r /etc/apt/trusted.gpg.d/wsl-transdebian.gpg

cat << EOF > /etc/apt/sources.list.d/wsl-transdebian.list
deb https://arkane-systems.github.io/wsl-transdebian/apt/ $(lsb_release -cs) main
deb-src https://arkane-systems.github.io/wsl-transdebian/apt/ $(lsb_release -cs) main
EOF

apt update
```

If you do not have lsb_release installed, you will need to manually substitute the distro name (e.g., "bullseye") in place of `$(lsb_release -cs)`.

## Contributing

To contribute packages to the wsl-transdebian repo, please fork this repository, place your packages in the "updates" folder within it, and then send me a pull request.

## Repository source

You can see the source for this repository at:

[https://github.com/arkane-systems/wsl-transdebian](https://github.com/arkane-systems/wsl-transdebian)
