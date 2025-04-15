# Docker CANopenEditor

This repository provides a Docker image bundling [CANopenEditor](https://github.com/robincornelius/canopeneditor), a GUI tool for editing CANopen EDS and DCF files.
Integration in VSCode is provided inside DevContainer if you are not confident with docker commands.

## Requirements

- Docker (or similar)
- VSCode with devcontainer extension installed
- x11 client

## Tested

- MacOS (XQuartz as x11 client)
- Linux (Ubuntu 24.04)

## License

This project is licensed under the MIT License. See the LICENSE file for details.
Note: This Docker image contains canopeneditor, which is licensed under the GNU General Public License v3 (GPLv3). You can find its source code and license here:
https://github.com/CANopenNode/CANopenEditor

No modifications have been made to canopeneditor in this image.

## Sample

demoDevice.eds and demoDevice.xdd are present for test purpose

### How to use (GUI)

Open the folder inside VSCode and open with DevContainer.
Or manually:

```shell
# Inside the container
mono ./CANopenEditor-v4/net481/EDSEditor.exe
```

### How to use (CLI)

```shell
# Inside the container
mono ./CANopenEditor-v4/net481/EDSSharp.exe --infile <eds_or_xdd_file> --outfile <output_filenam> --type <type_selected>
```
Example:
```shell
# Inside the container
mono ./CANopenEditor-v4/net481/EDSSharp.exe --infile demoDevice.xdd --outfile OD --type CanOpenNodeV4
```

Exporter types:
  - ElectronicDataSheet [.eds]
  - DeviceConfigurationFile [.dcf]
  - CanOpenNode [.h,.c]
  - CanOpenNodeV4 [.h,.c]
  - CanOpenXDDv1.0 [.xdd]
  - CanOpenNetworkv1.0 [.nxdd]
  - CanOpenXDDv1.1 [.xdd]
  - CanOpenXDDv1.1stripped [.xdd]
  - CanOpenXDCv1.1 [.xdc]
  - CanOpenNetworkXDDv1.1 [.nxdd]
  - CanOpenNetworkXDCv1.1 [.nxdc]
  - CanOpenNodeProtobuf(json) [.json]
  - CanOpenNodeProtobuf(binary) [.binpb]
  - DocumentationHTML [.html]
  - DocumentationMarkup [.md]
  - NetworkPDOReport [.md]
