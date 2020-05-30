# iASL Binaries for macOS

## Generated Executables

In the folder `binaries` are currently found the compiled executables of `iasl` directly from Intel's own sources.<br/>

Since the actual compiler name is the same, each version is differentiated with the release date from Intel.

## Intel ACPI References

The ACPI Component Architecture project is currently hosted over at https://www.acpica.org/<br/>

The sources themselves are accessible at https://www.acpica.org/downloads/

## Compiling iASL

According to user [acidanthera](https://github.com/acidanthera) page for [MaciASL tool](https://github.com/acidanthera/MaciASL), to build the latest ACPI compiler we need download the (latest) source release from [ACPICA.org](https://www.acpica.org/downloads/) and compile it via `Terminal.app` with the following command whilst in the unpacked sources folder:
```
CFLAGS="-mmacosx-version-min=10.7 -O3" \
LDFLAGS="-mmacosx-version-min=10.7" \
make iasl -j $(getconf _NPROCESSORS_ONLN)
```
The `iasl` binary will be later found at `./generate/unix/bin/` path where you launched the above command from.<br/>

To test that it has been compiled properly, run:

`./generate/unix/bin/iasl -v`

An example output of the 2020-05-28 release is:
```
Intel ACPI Component Architecture
ASL+ Optimizing Compiler/Disassembler version 20200528
Copyright (c) 2000 - 2020 Intel Corporation
```

Should one need to (manually) update `MaciASL.app` binaries with latest compiled ones, simply go to the `/MacOS/` folder of the tool and replace `iasl-stable` or `iasl-dev` with the respective versions needed.
