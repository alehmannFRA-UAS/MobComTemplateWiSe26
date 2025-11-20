# How to use the UERANSIM containers

Configuration is the most important part, and almost all of the problems are caused by an incorrect configuration (either UERANSIM or core network side).

- ```nr-ue``` accepts a UE configuration file as a parameter
- ```nr-gnb``` accepts a gNB configuration file as a parameter.

The syntax is the following:
```
nr-ue -c myconfig1.yaml
nr-gnb -c myconfig2.yaml
```

You can also set the number of UEs by:
```
nr-ue -c myconfig.yaml -n 10
```
This way, 10 UEs will start and run in the process. IMSI number is incremented by one for each of the UEs (starting from the IMSI specified in the config file). You can also override IMSI parameter in the config file over the command line by:
```
nr-ue -c myconfig.yaml -i imsi-286010000000001
```
or
```
nr-ue -c myconfig.yaml -n 10 -i imsi-286010000000001
```

# gNB

## Configuration
- mcc: Mobile Country Code value of HPLMN (Home PLMN).

- mnc: Mobile Network Code value of HPLMN (Home PLMN). MNC value can be either 2 digits or 3 digits. Note that 2-digit values are semantically different from 3-digit values. e.g 25 is different from 025. More details can be found on TS 23.501

- nci: This field specifies the NR Cell Identity. Also idLength specifies the bit length of the gNB ID which is a part of this NR Cell Identity. More on TS 38.413

- tac: Tracking Area Code (TAC) value for this cell.
- linkIp: Local IP for radio link simulation for this gNB. UE should connect to this IP address for radio simulation. The IP address must match with gnbSearchList parameter in the UE config file. Otherwise UE cannot connect to the gNB. By default we wrote 127.0.0.1 in the sample configuration files, but change this and gnbSearchList parameter according to your environment if you use UE and gNB in different machines.

- ngapIp: Local IP for N2 interface for this gNB. AMF will send SCTP packets to this IP address, therefore set this IP precisely. Otherwise AMF cannot connect to the gNB and SCTP timeout error occurs. By default we wrote 127.0.0.1 in the sample configuration files, but change this according to your environment if you use gNB and AMF in different machines. (Also our suggestion is always using UERANSIM and core network in different machines.)

- gtpIp: Local IP for N3 interface for this gNB. UPF will send GTP packets to this IP address, therefore set this IP precisely. Otherwise UPF cannot send datagrams to the gNB and data plane functions cannot work. By default we wrote 127.0.0.1 in the sample configuration files, but change this according to your environment if you use gNB and UPF in different machines. (Also our suggestion is always using UERANSIM and core network in different machines.)

- gtpAdvertiseIp: If you want to separate GTP listening address and external access address, you can set this value to override Downlink User-Plane Transport Layer Address which is advertised to UPF. This field is optional and not required for most of the people. It is especially useful in case of a NAT between gNB and UPF. We didn't include this field in the sample config files.

- amfConfigs: List of AMF IP address and port information for N2 (NGAP) interface. This is the other endpoint of what you set in ngapIp address. This time you should set this value as AMF's IP address. By default we wrote 127.0.0.X in the sample configuration files, but change this according to your environment if you use gNB and AMF in different machines. This value is normally a list, but currently only first specified AMF is used. More complex AMF selection mechanism will be implemented in the future.

- slices: This field is explained in the UE configurations. And it is the supported list of slices by the gNB.

- ignoreStreamIds: Some core networks may not handle SCTP stream numbers properly. Set this field to true if you want to ignore such errors.

# Configuration guide
Add your custom configuration file to the ueransim gnb container like:
```yaml
services:

 gnb:
  ...
    configs:
      - source: gnb_config
        target: /UERANSIM/config/gnb.yaml
...
configs:
  gnb_config:
    file: /path/to/file/gnb.yaml
```

Specify the command to run by the ueransim gnb container like:
```yaml
services:
  ...
  gnb:
  ...
    command: "-c /UERANSIM/config/gnb.yaml"
```

# UE

## Configuration
- supi: IMSI number of the UE must be written in this field. Note that we only support IMSI as a SUPI, i.e NAI is not supported. This field is mandatory except for emergency registration.

- mcc: Mobile Country Code value of HPLMN (Home PLMN). This value must be consistent with SUPI.

- mnc: Mobile Network Code value of HPLMN (Home PLMN). This value must be consistent with SUPI. MNC value can be either 2 digits or 3 digits. Note that 2-digit values are semantically different from 3-digit values. e.g 25 is different from 025. More details can be found on TS 23.501

- key: This is the permanent subscription key assigned for this specific UE.

- op: Operator code value (in either OP or OPC) must be written here. You should set opType as OP if you write an OP value here, and you should set opType as OPC if you write an OPC value here. You can either use OP or OPC keys.

- amf: Authentication Management Field (AMF) must be written here. Note that this is a different thing from core network function AMF (Access and Mobility Management Function)

- imei: IMEI number of the device. IMEI is used if no SUPI provided and for emergency registration etc. This value is generally not used.

- imeiSv: IMEISV number of the device. IMEISV is used if no SUPI and IMEI provided and for emergency registration etc. This value is generally not used.

- gnbSearchList: This is the list of IP addresses of gNB for radio link simulation. You can write multiple IP addresses for multiple gNBs. UE will try to pick some gNB from this list. The IP address must match with linkIp parameter in the gNB config file. Otherwise UE cannot connect to the gNB. By default we wrote 127.0.0.1 in the sample configuration files, but change this and linkIp parameter according to your environment if you use UE and gNB in different machines.

- uacAic: Unified Access Control (UAC), Access Identities Configuration (AIC) shall be configured in this field. mps stands for Multimedia Priority Service and mcs stands for Mission Critical Service. See TS 31.102 for UAC AI configurations.

- uacAcc: Unified Access Control (UAC), Access Control Class (ACC) shall be configured in this field. normalClass takes the value in range [0, 9], and the classes from 11 to 15 are for high priority access. See TS 31.102 for UAC ACC configurations.

- sessions: This is the list of initial PDU sessions. These sessions are automatically established after the UE successfully registers to the 5G core network. You can add multiple PDU sessions to this list. (No more than 15). If you don't want an initial PDU session, you can completely delete the sessions parameter. Sessions has type, apn and slice parameters. Only IPv4 is supported for now as a PDU session type. apn field is optional and specifies the Access Point Name. slice parameter is optional and specifies the S-NSSAI for this specific PDU session. Also sd parameter is optional as well, but sst is always required if the slice parameter is included. You can delete optional parameters or set null to the relevant fields.

- configured-nssai: Configured NSSAI for this UE by HPLMN (Home PLMN). Content of the NSSAI is already explained above.

- default-nssai: Default Configured NSSAI for this UE device. Content of the NSSAI is already explained above.

- integrity/ciphering: Here you can set supported integrity and ciphering algorithm for this specific UE. Normally UERANSIM supports all of the algorithms but you can disable some of them manually by this configuration.

- integrityMaxRate: This fields specifies the integrity protection maximum data rate for user plane for this UE. Possible values are 64kbps and full as specified by TS 24.501.

- tunName: You can customize the name of the auto created TUN interface. Given value specifies a prefix for the actual name. This value is optional (Default is uesimtun)

# Configuration guide
Add your custom configuration file to the ueransim ue container like:
```yaml
services:

 ue:
  ...
    configs:
      - source: gnb_config
        target: /UERANSIM/config/ue.yaml
...
configs:
  ue_config:
    file: /path/to/file/ue.yaml
```

Specify the command to run by the ueransim ue container like:
```yaml
services:
  ...
  ue:
  ...
    command: "-c /UERANSIM/config/ue.yaml"
```

## Using the UE's connection
You can use the emulated UE connection by connecting to the UE container:
```shell
# connect to the UE container
docker exec -it ue bash

# Use the TUN interface to test the UE connection
ping -I uesimtun0 8.8.8.8
```

## Command Line Options
We provide nr-cli tool for both gNB and UEs.

NOTE: UE and gNB have different CLI commands. For example in gNB you can check the AMF connection status, or in UE you can trigger de-registration. More details are explained in the present document.

Usage:
```bash
nr-cli <node-name>
```
Here you need to replace <node-name> with a UE or gNB name. For example:
```bash
nr-cli imsi-001010000000001
```
You can query the current UE and gNBs in the environment using:
```bash
$ nr-cli --dump

imsi-001010000000001
imsi-001010000000002
imsi-001010000000003
```
After running ```nr-cli <node-name>``` command, an interactive shell will be open if given node is present and running in the environment. You can now execute further commands for this node.

To see available commands, use commands.

For Example:
```bash
user@pc:~/UERANSIM/build$ ./nr-cli UERANSIM-gnb-001-01-1
--------------------------------------------------------------------------------------------
$ commands
amf-info | Show some status information about the given AMF
amf-list | List all AMFs associated with the gNB
info     | Show some information about the gNB
status   | Show some status information about the gNB
ue-count | Print the total number of UEs connected the this gNB
ue-list  | List all UEs associated with the gNB
--------------------------------------------------------------------------------------------
```
You can further investigate usage and help information for sub-commands.

The commands available for gnb are:
```bash
$ commands
status
info
amf-list
amf-info <amf-id>
ue-list
ue-count
ue-release <ue-id>
```

The commands available for ue are:
```bash
$ commands
status
info
timers
ps-establish
ps-release
ps-release-all
ps-list
deregister
rls-state
coverage
```

For example:
```bash
$ amf-info --help
$ ue-list --version
```
etc.

You can also use ```-e/--exec``` option if you want to directly execute the command instead of using the interactive shell.

For example:
```bash
nr-cli imsi-001010000000001 --exec "status"
```
For more details, see ```nr-cli --help```