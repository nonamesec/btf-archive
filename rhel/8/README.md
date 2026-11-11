# Pinned RHEL 8 build BTF

These archives contain pinned BTF baselines for RHEL 8.1 and RHEL 8.10
(Ootpa), following the RHEL 10 archive convention. They contain kernel
type metadata, not sensor configuration or credentials.

## RHEL 8.10 x86_64

`x86_64/4.18.0-553.172.1.el8_10.x86_64.btf.tar.xz` contains the native
`/sys/kernel/btf/vmlinux` from an x86_64 Red Hat Enterprise Linux 8.10
host running kernel `4.18.0-553.172.1.el8_10.x86_64`.

The snapshot was extracted on 2026-11-11 from the IC-82140
`btf-rhel8-ic82140` lab instance, provisioned from official Red Hat AMI
`ami-03288f7877c413c29` in us-east-1 (AMI owner `309956199498`, image
`RHEL-8.10.0_HVM-20261013-x86_64-2315-Hourly2-GP3`). The OS, running
kernel release, and architecture were verified on the host.

| File | SHA-256 |
| --- | --- |
| Compressed `.btf.tar.xz` | `181ae5a263a27ce3f49ba2f2db0d71edc9fd6f533de1f486515d5be8d1eb40bb` |
| Uncompressed BTF | `18b4218419111665f09d97f11170ad4d037be9a74c3a60a4cb8264c5cdf2e236` |

The uncompressed file is 4,265,079 bytes. The archive has one member,
`4.18.0-553.172.1.el8_10.x86_64.btf`.

## RHEL 8.10 ARM aarch64

`aarch/4.18.0-553.172.1.el8_10.aarch64.btf.tar.xz` contains the `.BTF`
section from the AArch64 ELF `vmlinux` in the official Red Hat
`kernel-debuginfo-4.18.0-553.172.1.el8_10.aarch64.rpm` package, extracted
on 2026-11-11. The package was downloaded from
`rhel-8-baseos-rhui-debug-rpms` using `dnf --forcearch=aarch64`; it was
not installed. RPM verification reported `digests signatures OK`, and
the ELF machine was verified as `EM_AARCH64` (183).

| File | SHA-256 |
| --- | --- |
| Source RPM | `48cbc6f2a5100b4bb49a8194a571a05860bcbba6db94b4470da082fcf3da18a8` |
| Compressed `.btf.tar.xz` | `1043deb8ee3e35bbb8de3851c8eec83e140dd915355015a04738ecfbc1d69e57` |
| Uncompressed BTF | `77a27e8e11e01ebcaca0933b49c7e0b4caec29b4020acbb53c0143556469304d` |

The uncompressed file is 4,029,232 bytes. The archive has one member,
`4.18.0-553.172.1.el8_10.aarch64.btf`.

## RHEL 8.1 snapshots

The following BTF snapshots were imported on 2026-11-11 from
[Aqua Security BTFHub Archive](https://github.com/aquasecurity/btfhub-archive/tree/8c1638259de2830e4c217cff2ea49bca2b2041e4)
at commit `8c1638259de2830e4c217cff2ea49bca2b2041e4`. Architecture and kernel release
are taken from the upstream paths. These are upstream BTF snapshots,
not native BTF extracted from the RHEL 8.10 lab described above.
The upstream [Apache 2.0 license](BTFHUB-LICENSE) is included.

The BTF bytes are unchanged. Only the tar metadata and compression were
normalized to the archive convention below. Downloaded archives were
verified against their upstream Git blob IDs before repacking.

### 4.18.0-147.8.1.el8_1.aarch64

`aarch/4.18.0-147.8.1.el8_1.aarch64.btf.tar.xz` contains one member,
`4.18.0-147.8.1.el8_1.aarch64.btf` (27,031,996 bytes).

[Upstream archive](https://github.com/aquasecurity/btfhub-archive/blob/8c1638259de2830e4c217cff2ea49bca2b2041e4/rhel/8/arm64/4.18.0-147.8.1.el8_1.aarch64.btf.tar.xz)
(Git blob `ebc8d1f15a21516e960e70d3cdc5053c3c84b485`).

| File | SHA-256 |
| --- | --- |
| Upstream `.btf.tar.xz` | `c748506535a01d93eb630fd802445e23fa79e49f85be8723a9e48ba05bf82aaa` |
| Repacked `.btf.tar.xz` | `aa9fa357affc7851b94281a1265482cd92bd6d698932e5575f59372024fe3870` |
| Uncompressed BTF | `5dc8b1298e8119f4eaa9702a41f375f20b5ef7cf3e7b8968062a7bcef210cfaf` |

### 4.18.0-147.57.1.el8_1.x86_64

`x86_64/4.18.0-147.57.1.el8_1.x86_64.btf.tar.xz` contains one member,
`4.18.0-147.57.1.el8_1.x86_64.btf` (44,382,648 bytes).

[Upstream archive](https://github.com/aquasecurity/btfhub-archive/blob/8c1638259de2830e4c217cff2ea49bca2b2041e4/rhel/8/x86_64/4.18.0-147.57.1.el8_1.x86_64.btf.tar.xz)
(Git blob `61a08af7550811904196c0cbbf4f8021313bfec8`).

| File | SHA-256 |
| --- | --- |
| Upstream `.btf.tar.xz` | `ce2b99638277c170984b6077a751b351aeb8f5a12d16a8c095c32bba5597df0d` |
| Repacked `.btf.tar.xz` | `f7d3e6cef8e3217c96b5f88d33e60fc0389d11bbaa8a83c138d6b07ae1000865` |
| Uncompressed BTF | `af0b9db62c28d2e8abcd577b79335a9b0c3c5c3f45198e97d5274d37e724d573` |

## Format and validation

All archives use USTAR format with owner/group 0, empty owner/group
names, mode 0644 and timestamp 0, compressed with XZ preset 9. Archive
metadata, compressed and uncompressed SHA-256 checksums, BTF parsing,
and `vmlinux.h` generation with `bpftool` were verified for all four files.

These snapshots can generate compile-time `vmlinux.h` for a sensor's
RHEL 8 build. They are pinned baselines, not a claim of compatibility
with every RHEL 8 kernel. Runtime CO-RE relocation should use the target
host's native BTF when available. Sensor compilation and runtime capture
validation for each architecture remain separate requirements.

To add another baseline, extract native BTF from a verified RHEL 8 host
or the `.BTF` section from the matching official kernel debuginfo ELF,
or import an exact snapshot from a pinned BTFHub Archive revision.
Record the exact kernel release, architecture, source provenance, and
both checksums. Consumers should pin the archive commit and verify its
checksum.
