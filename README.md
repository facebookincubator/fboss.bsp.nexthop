# fboss.bsp.nexthop

Board support package (BSP) code for FBOSS switches developed by Nexthop.

This repository packages the kernel drivers that FBOSS platform software relies
on, building them into an installable kmods RPM.

## Building

Build the kernel modules against the running kernel's headers:

```bash
./build.sh          # build
./build.sh clean    # clean build artifacts
```

Build the installable RPM (requires `rpmbuild` and `kernel-devel`):

```bash
./build_rpm.sh
```

The resulting package is written under `rpmbuild/RPMS/<arch>/` and installs the
modules to `/lib/modules/<kver>/extra/` with the manifest and helper scripts
under `/usr/local/nexthop_bsp/<kver>/`.

`distro_build.sh` is the entry point for the FBOSS distro image build pipeline:
it installs the build dependencies from the RPM spec, builds the RPM, and stages
it as a tarball under `/output`.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for the contribution process and
[CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) for community expectations.

## License

This project is licensed under the GNU General Public License, version 2,
matching [fboss.bsp.kmods](https://github.com/facebookincubator/fboss.bsp.kmods).
See [LICENSE](LICENSE) for the full license text.
