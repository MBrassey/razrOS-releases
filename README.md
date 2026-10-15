# razrOS releases

Signed packages of razrOS, a Linux distribution for the Motorola razr
fold 2026 ("blanc"). Phones running razrOS update from here: `razr-update`
fetches the package database and the packages from the assets of the
release named after the architecture, [`aarch64`](../../releases/tag/aarch64).

## On a phone

razrOS's `/etc/pacman.d/razros-mirrorlist` names this repository:

```
Server = https://github.com/MBrassey/razrOS-releases/releases/download/$arch
```

pacman accepts the razros packages and their database only with a good
signature from the razrOS repository key:

```
B199472E477652B2E5214B546038B03CB37B1744
```

The `razros-keyring` package carries that key, and each phone adds it to
its own keyring at first boot.

## Checking a file by hand

```sh
gpg --import razros.gpg                        # from the release
gpg --verify razr-update-0.1.0-1-any.pkg.tar.xz.sig razr-update-0.1.0-1-any.pkg.tar.xz
```

## Licenses and sources

razrOS's own packages (`razr-*`, `razros-keyring`) are published under the
licenses in their package metadata. The release also carries
`THIRD-PARTY-NOTICES.md`: the Rust crates and the musl C library compiled
into razrOS's programs, with their license texts.

Third-party software packaged here, and where its source is:

| Package | License | Source |
|---|---|---|
| linux-razr-vendor | GPL-2.0-only | Motorola's [kernel-common](https://github.com/MotorolaMobilityLLC/kernel-common), with razrOS's patches, configuration and build script in `linux-razr-vendor-VERSION-source.tar.xz` (in the release; `SOURCE.md` inside names the exact upstream tag and commit) |
| sing-box-bin | GPL-3.0-or-later | SagerNet's [sing-box](https://github.com/SagerNet/sing-box), the release binary of the version in the package name, unchanged |
| hexagonrpc | GPL-3.0-or-later | [linux-msm/hexagonrpc](https://github.com/linux-msm/hexagonrpc), the tag of the version in the package name |
| qrtr, pd-mapper, rmtfs, tqftpserv | BSD-3-Clause | [linux-msm](https://github.com/linux-msm), the tags of the versions in the package names |
| vulkan-freedreno-kgsl | MIT | [Mesa](https://mesa3d.org), the version in the package name |
| razr-netguard-rules | CC-BY-SA-4.0 (the rule data) | SagerNet's [sing-geosite](https://github.com/SagerNet/sing-geosite) rule sets |
| word lists in razr-deck | SCOWL (its copyright notice is in the package) | [SCOWL](http://wordlist.aspell.net) |
| the Inter font in razr-shell and razr-unlock | OFL-1.1 | [Inter](https://rsms.me/inter) |
