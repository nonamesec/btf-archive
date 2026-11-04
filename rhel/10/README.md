# Pinned RHEL 10 build BTF

`x86_64/6.12.0-211.53.1.el10_2.x86_64.btf.tar.xz` contains the native
`/sys/kernel/btf/vmlinux` from an x86_64 Red Hat Enterprise Linux 10.2
(Coughlan) host running kernel `6.12.0-211.53.1.el10_2.x86_64`.

The snapshot was extracted on 2026-11-04 from the IC-81277 `sensor-rhel10`
lab instance, provisioned from official Red Hat AMI `ami-038a727c6c8b5450a`
in us-east-1 (AMI owner `309956199498`). It contains kernel type metadata,
not sensor configuration or credentials.

| File | SHA-256 |
| --- | --- |
| Compressed `.btf.tar.xz` | `92b7987998b84a9613e5d8fad197933ce7fd45c7c02d25411ab79754caf7cbc0` |
| Uncompressed BTF | `040d3f64b8b31b8e92ee06d90a1c69872b33058a3a63f36e48391e3d9b82c78e` |

The uncompressed file is 5,655,035 bytes. The archive has one member,
`6.12.0-211.53.1.el10_2.x86_64.btf`. It uses USTAR format with owner/group 0,
mode 0644 and timestamp 0, compressed with XZ preset 9.

This snapshot can generate compile-time `vmlinux.h` for the sensor's RHEL 10
build. Runtime CO-RE relocation should use the target host's native BTF.
Capture paths that copy kernel structures still require runtime validation.

To add another baseline, extract `/sys/kernel/btf/vmlinux` from a verified
RHEL 10 host, record the exact kernel release and architecture, and archive
it with a versioned filename. Record both checksums and source provenance.
Consumers should pin the archive commit and verify its checksum.
