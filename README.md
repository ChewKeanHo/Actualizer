# (Holloway) Chew Kean Ho's Actualizer

[![Actualizer](src/icons/animated-banner_1200x100.svg)](#)

Tired of bloated OS images and cumbersome installers? Want to build the
smallest possible Debian OS while preserving full upstream compliance and
trust? Meet **Actualizer — a simple, single shell script solution designed to
empower developers and embedded engineers to create lean, secure, upstream
compliant, and customizable Debian operating systems from the ground up.**

Unlike traditional Debian ISO installers, Actualizer strips away the excess.
Leveraging Debian's `debootstrap` and rigorous curation, it constructs a
terminal-only, near-bare-metal OS with an uncompromised Chain of Trust to the
upstream Debian repositories. Perfect for embedded systems, IoT devices, or
high-performance server/desktop environments, Actualizer delivers:

1. **Ultra-Minimal Footprint** - Remove all non-essential packages—no GUI,
    no bloat, just a pristine Debian core.
2. **Upstream Compliance** - Maintain 100% compatibility with Debian’s
   ecosystem while ensuring security and auditability.
3. **Embedded-First Design** - Optimized for resource-constrained hardware,
   yet scalable for desktop/server use cases.
4. **Transparent & Reproducible** - A single script, operable via Debian Live
   ISO, ensures simplicity and reproducibility for developers.

Join my community-driven movement to redefine minimalism in Debian.

Build smaller. Build smarter. Build with (Holloway) Chew, Kean Ho's Actualizer.

> **WARNING DISCLAIMER**
>
> Actualizer is **NOT** for the faint of heart. Designed for OS engineers
> and Linux veterans, it requires comfort with terminal-only interfaces and
> manual system customization. But for those who demand absolute control over
> their stack, Actualizer unlocks unparalleled efficiency and trust.
>
> Here's how an end product looks like in QEMU:
>
> [![terminal-only-qemu](src/screenshots/terminal-only-qemu.jpg)](#)




## Technical Features

[![Actualizer](src/icons/animated-banner_1200x100.svg)](#)

Acutalizer is an user-prompting automata so you are required to response on
screen setup accordingly before paritition mounting steps. Otherwise, you're
good!

Here are the base features installed using this script into your target:

* **Tri-Partitions** - `EFI` (UEFI,1G), `BOOT` (LEGACY,1G), `CORE` (DATASTORE,100%FREE)
* **Single Architecture** - depending on your selected Live OS DVD. Only 1
                            is installed.
* **Cryptsetup Datastore** - `CORE` partition is encrypted with the latest
                             acceptable algorithm.
* **LVM Disk Management** - `CORE` partition is managed by `lvm` inside the
                             cryptsetup encrypted layer for data integrity &
                             maintenances.
* **SecureBoot Enabled** - supported by default.
* **Single Language** - only 1 language installed.
* **Single Keyboard Configuration** - only 1 keyboard configuration installed.
* **Wifi + Ethernet Basic Network** - basic wifi (`iwd`) and ethernet
                                      (`connman`) network (`iproute2`)
                                      configuration.
* **No Text Editor** - Install only your desired one on your own.
* **NFTables Firewall** - Latest Linux firewall.
* **Track Stable Upstream**  - Using `stable` against
                               `https://deb.debian.org/debian/`.
* **Track Stable Security**  - Using `stable-security` against
                               `https://security.debian.org/debian-security`
* **Track Stable Updates**   - Using `stable-updates` against
                               `https://deb.debian.org/debian/`.
* **Track Stable Backports** - Using `stable-backports` against
                              `https://deb.debian.org/debian/`.
* **Enables `contrib`** - Enables `contrib` series by default.
* **Enables `non-free`** - Enables `non-free` series by default.
* **Enables `non-free-firmware`** - Enables `non-free-firmware` series by
                                    default.
* **Using Debian Signed Kernel** - Only uses signed kernel for
                                   SecureBoot (Security).
* **Using Debian Signed Bootloader** - Only uses signed bootloader for
                                       SecureBoot (Security).
* **Configured `/etc/hostname`** - hostname configured for network from the
                                   get-go.
* **Create 1 non-sudo User** - create 1 non-sudo User with home directory by
                               default.
* **Configure root User** - configure root user for basic security.
* **No Swap Partition/File** - for SecureBoot (security).
* **Debian CA Certificates Installed** - for seamless secured network
                                         connectivity.
* **Debian APT HTTPS Transport Installed** - for securing upstream supply chain.




## How-to Use

[![Actualizer](src/icons/animated-banner_1200x100.svg)](#)



### 1. Boot the Debian Live DVD (not Installer) ISO

You need to download the Debian Live DVD (not the Installer DVD). When booted
up, it **MUST** show **Live Boot Option**. Otherwise, you got the wrong image
so please procure it.

[![live-dvd](src/screenshots/live-dvd.jpg)](#)


Available URLs:

* **Debian Live DVD Official Page** - https://www.debian.org/CD/live/
* **Debian Live DVD Wiki Page** - https://wiki.debian.org/DebianLive
* **Debian Live DVD (amd64) ISO Repository** - https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/



### 2. Switch to Root Account

Once you're on the live DVD, switch to root account by simply running the
following command (no password required):

```
$ sudo su
```

[![execute-actualizer](src/screenshots/switch-to-root.jpg)](#)



### 3. Download the Script

Proceed to download a copy of the script from one of my release servers
across the Globe:

```
$ curl --tlsv1.2 --location --output "/actualizer.sh" --url [URL]
```

Available URLs:

* **Zenodo (Global)** - `https://`
* **GitHub (Global)** - `https://github.com/ChewKeanHo/Actualizer/releases/download/[VERSION]/debian-install.sh`



### 4. Run the Script

Now that we have the script available for execution, proceed to run it. This
script will tell you what is required on-screen (e.g. what dependencies are
missing, checking qualified cryptography random generator, etc). Please
Respond accordingly.

> **SIDE-NOTE**:
>
> For dependencies, you can safely do `$ apt install debootstrap -y` before
> executing the script. For some reason, Debian did not ship the package
> enabled by default.

```
$ chmod +x ./actualizer.sh   # NOTE: Run once to make it executable
$ ./actualizer.sh
```

[![execute-actualizer](src/screenshots/execute-script.jpg)](#)




## Maintainers' Supports

[![Actualizer](src/icons/animated-banner_1200x100.svg)](#)

You can procure my sponsorship token here
(https://www.hollowaykeanho.com/en/stores/). Financial supports are always
appreciated.



### Technical Requirements

To be determined. Right now, its CI build infrasturcture and documentations
must be up first before anything else. Stay tuned.




## License

[![Actualizer](src/icons/animated-banner_1200x100.svg)](#)

Actualizer is licensed under
[(Holloway) Chew, Kean Ho's Liberal License](LICENSE.txt).
