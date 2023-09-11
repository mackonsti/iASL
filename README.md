# iASL Binaries for macOS

## Generated Executables

In the folder `binaries` are currently found the compiled executables of `iasl` directly from Intel's own sources.

Since the actual `iasl` compiler name is the same through each new release, each version stored here is differentiated with the release date from Intel. Just download the needed binary and rename it back to `iasl` for using it later.

## Intel ACPI References

The **ACPI Component Architecture** project is currently hosted over at https://www.acpica.org/<br/>

The sources themselves are freely accessible at https://www.acpica.org/downloads/ as **acpica-unix-YYYYMMDD.tar.gz** files (Intel license).

## Direct Access to the Public ACPICA Git Repository

According to Intel's own pages, the entire source code for the ACPICA project is maintained under the `git` version control system in a single repository. This repository can be directly accessed via `git://github.com/acpica/acpica.git`

## Compiling iASL

According to user [acidanthera](https://github.com/acidanthera)'s page for [MaciASL tool](https://github.com/acidanthera/MaciASL), to build the latest ACPI compiler we need download the (latest) source release from [ACPICA.org](https://www.acpica.org/downloads/) and compile it via `Terminal.app` with the following command whilst in the unpacked sources folder:
```
CFLAGS="-mmacosx-version-min=10.7 -O3" \
LDFLAGS="-mmacosx-version-min=10.7" \
make iasl -j $(getconf _NPROCESSORS_ONLN)
```
The `iasl` binary will be later found at `./generate/unix/bin/` path where you launched the above command from. To test that it has been compiled properly, run:

`./generate/unix/bin/iasl -v`

An example output of the **2020-05-28** release (based on source **acpica-unix-20200528.tar.gz**) is:
```
Intel ACPI Component Architecture
ASL+ Optimizing Compiler/Disassembler version 20200528
Copyright (c) 2000 - 2020 Intel Corporation
```

## Using compiled binaries with MaciASL

The developers are releasing, from time to time, updates to their main tool [MaciASL](https://github.com/acidanthera/MaciASL/releases) that includes the latest compiled binaries at the _time_ of each release.

Should one need to (manually) update `MaciASL.app` binaries with latest (or previous) compiled `iasl` versions, one can simply go to the `/MacOS/` folder of the tool and replace `iasl-stable` or `iasl-dev` with the respective versions needed.

Remember that `iasl-dev` is the binary that's supposed to be the latest available, so that compatibility is kept with `iasl-stable` and `iasl-legacy` so you are advised to only update `iasl-dev` really.
