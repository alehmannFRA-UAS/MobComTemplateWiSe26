# How to use the PacketRusher container

### gtp5g kernel dependency

The project uses [PacketRusher](https://github.com/HewlettPackard/PacketRusher) using the packetrusher image from [docker-hub](https://hub.docker.com/r/fgftk/packetrusher).

This image depends on a kernel module being installed on the host machine, the `free5gc's gtp5g kernel module`.

## Configuration
### Configuration File
You must configure the parameters that'll be used by your simulated UE(s) and gNodeB(s) prior to running PacketRusher.

#### gNodeB Configuration:
- controlif: IP and Port for N2 interface for gNodeB. PacketRusher will use IP and Port to communicates with AMF and receive NAS/NGAP packets from AMF via SCTP socket. It's usually your machine's ip. Change depending on your environment.

- dataif: IP and Port for N3 interface for gNodeB. PacketRusher will use IP and Port to communicates with UPF and receive GTP packets from UPF via UDP socket. It's usually your machine's ip. Change depending on your environment.

- plmnlist: contains MCC (Mobile Country Code value)/ MNC (Mobile Network Code), TAC (Tracking Area Code) and gnbid information. These information must be consistent with 5G Core, AMF and UE's configuration.

- slicesupportlist: The list of slices supported by this gNodeB by tracking area. It's usually the slice that you will want to connect in the 5G Core. sd field is optional.

#### UE Configuration:
- msin: MSIN number of the UE. If your UE's SUPI is imsi-999700000000120, then MSIN will be "0000000120", MCC = "999" and MNC = "70". The MCC and MNC must be included in hplmn field.

- key: Permanent Subscription Key. This is the key that must have been provisioned for the UE. This field is used for authentication of UE. Currently the PacketRushers only supports 5G-AKA authentication method.

- opc: Operator Code Value. This is the opc that must have been provisioned for the UE. This field is used for authentication of UE. The usage of an op is not yet supported.

- amf: Authentication Management Field (AMF). This is the AMF value that must have been configured for the UE. This field is used for authentication of UE.

- sqn: Sequence Number. The default value will work in the basics case, e.g, registration of UE. If you want to trigger resynchronization of Sequence Number (SQN) in authentication process with 5GC, try to change this value.

- dnn: refers information about PDU Session. In this case, specifies the data network for the PDU Session and can be used for SMF/UPF selection.

- hplmn: the MCC and MNC part of IMSI information for the UE.

- snssai: refers information about PDU Session. In this case, specifies the slice for the PDU Session and can be used for SMF/UPF selection. sd field is optional.

#### AMF Configuration:
- Ip: The AMF's IP Address on N2.

- Port: The AMF N2 endpoint's port, the default is 38412.

### Configuration example
Here is an example of PacketRusher configuration for the following setup:

- 5G SA Core Network
- MCC is 999, MNC is 70
- Default slice is SST 01 SD 000001 (Slice N°01-000001)

#### AMF/UPF Configuration
In this 5G Core under test, N2 and N3 are the same network:

| Network Function | NETWORK NAME | IP ADDRESS |
|-|-|-|
| AMF | N2 | 192.168.11.30 |
| UPF |	N3 | 192.168.11.31 |

#### gNodeB

| | INTERFACE NAME | NETWORK NAME | IP ADDRESS |
|-|-|-|-|
| gNodeB | controlif | N2 | 192.168.11.13 |
| gNodeB | dataif | N3 | 192.168.11.13 |

In this setup, PacketRusher's gNodeB uses the same IP/network to reach both AMF and UPF.
The IP specified in controlif should be able to reach AMF's N2 interface, and the IP specified in dataif should be able to access UPF's N3 data interface.

#### UE
In this setup, we assume the following SUPI (imsi-999700000000120) was provisioned in the 5G Core:

| Device | MCC | MNC | MSIN | KEY | OPC | AMF | SQN |
|-|-|-|-|-|-|-|-|
| UE0 | 999 | 70 | 0000000120 | 00112233445566778899AABBCCDDEEFF | 00112233445566778899AABBCCDDEEFF | 8000 | 00000000 |

If you are running PacketRusher with ```--multi-ue --number-of-ues 5```, then you shall have 5 UEs provisioned with exactly the same provisioning information, but with their MSIN being sequential from 0000000120 to 0000000124:

| Device | MCC | MNC | MSIN | KEY | OPC | AMF | SQN |
|-|-|-|-|-|-|-|-|
| UE0 | 999 | 70 | 0000000120 | 00112233445566778899AABBCCDDEEFF | 00112233445566778899AABBCCDDEEFF | 8000 | 00000000 |
| UE1 | 999 | 70 | 0000000121 | 00112233445566778899AABBCCDDEEFF | 00112233445566778899AABBCCDDEEFF | 8000 | 00000000 |
| UE2 | 999 | 70 | 0000000122 | 00112233445566778899AABBCCDDEEFF | 00112233445566778899AABBCCDDEEFF | 8000 | 00000000 |
| UE3 | 999 | 70 | 0000000123 | 00112233445566778899AABBCCDDEEFF | 00112233445566778899AABBCCDDEEFF | 8000 | 00000000 |
| UE4 | 999 | 70 | 0000000124 | 00112233445566778899AABBCCDDEEFF | 00112233445566778899AABBCCDDEEFF | 8000 | 00000000 |

#### YAML Example
```shell
# PacketRusher Simulated gNodeB Configuration
gnodeb:
  # IP Address on the N2 Interface (e.g. used between the gNodeB and the AMF)
  controlif:
    ip: "127.0.0.1"
    port: 9487

  # IP Address on the N3 Interface (e.g. used between the gNodeB and the UPF)
  dataif:
    ip: "127.0.0.1"
    port: 2152

  # gNodeB's Identity
  plmnlist:
    mcc: "999"
    mnc: "70"
    tac: "000001"
    gnbid: "000008"

  # gNodeB's Supported Slices
  slicesupportlist:
    sst: "01"
    sd: "000001" # optional, can be removed if not used

# PacketRusher Simulated UE Configuration
ue:
  # UE's Identity, frequently called IMSI in 4G and before
  # IMSI format is "<mcc><mnc><msin>"
  # In 5G, the SUPI of the UE will be "imsi-<mcc><mnc><msin>""
  # With default configuration, SUPI will be imsi-999700000000120
  hplmn:
    mcc: "999"
    mnc: "70"
  msin: "0000000120"

  # In 5G, the UE's identity to the AMF as a SUCI (Subscription Concealed Identifier)
  #
  # SUCI format is suci-<supi_type>-<MCC>-<MNC>-<routing_indicator>-<protection_scheme>-<public_key_id>-<scheme_output>
  # With default configuration, SUCI sent to AMF will be suci-0-999-70-0000-0-0-0000000120
  #
  # SUCI Routing Indicator allows the AMF to route the UE to the correct UDM
  routingindicator: "0000"
  #
  # SUCI Protection Scheme: 0 for Null-scheme, 1 for Profile A and 2 for Profile B
  protectionScheme: 0
  #
  # Home Network Public Key
  # Ignored with default Null-Scheme configuration
  homeNetworkPublicKey: "5a8d38864820197c3394b92613b20b91633cbd897119273bf8e4a6f4eec0a650"
  #
  # Home Network Public Key ID
  # Ignored ith default Null-Scheme configuration
  homeNetworkPublicKeyID: 1
  
  # UE's SIM credentials
  key: "00112233445566778899AABBCCDDEEFF"
  opc: "00112233445566778899AABBCCDDEEFF"
  amf: "8000"
  sqn: "00000000"

  # UE will request to establish a data session in this DNN (APN)
  dnn: "internet"
  # in the following slice
  snssai:
    sst: "01"
    sd: "000001" # optional, can be removed if not used

  # The UE's security capabilities that will be advertised to the AMF
  integrity:
    nia0: false
    nia1: false
    nia2: true
    nia3: false
  ciphering:
    # For debugging Wireshark traces, NEA0 is recommended, as the NAS messages 
    # will be sent in cleartext, and be decipherable in Wireshark.
    nea0: true
    nea1: false
    nea2: true
    nea3: false

# List of AMF that PacketRusher will try to connect to
amfif:
  - ip: "127.0.0.1"
    port: 38412
logs:
  level: 4
```

# Configuration guide

You can specify FQDNs for `gnodeb controlif` (gNB N2), `gnodeb dataif` (gNB N3) and `amfif ip` (AMF N2) in the configuration file and the entrypoint of this image will parse them.
```yaml
gnodeb:
  controlif:
    ip: gnb.packetrusher.org
    port: 38412
```

Add your custom configuration file to the packetrusher container like:
```yaml
services:
  ...
  packetrusher:
  ...
    configs:
      - source: packetrusher_config
        target: /PacketRusher/config/packetrusher.yaml
...
configs:
  packetrusher_config:
    file: /path/to/file/packetrusher.yaml
```

Specify the command to run by the packetrusher container like:
```yaml
services:
  ...
  packetrusher:
  ...
    command: "--config /PacketRusher/config/packetrusher.yaml ue"
```

## Using the UE's connection

You can use the emulated UE connection by using the VRF.

Check the logs of the PacketRusher container to see the VRF identifier:
```bash
docker logs -f packetrusher
time="2025-08-31T06:27:48Z" level=info msg="Loaded config at: /PacketRusher/config/packetrusher.yaml"
time="2025-08-31T06:27:48Z" level=info msg="PacketRusher version 1.0.1"
time="2025-08-31T06:27:48Z" level=info msg=---------------------------------------
time="2025-08-31T06:27:48Z" level=info msg="[TESTER] Starting test function: Testing an ue attached with configuration"
time="2025-08-31T06:27:48Z" level=info msg="[TESTER][UE] Number of UEs: 1"
time="2025-08-31T06:27:48Z" level=info msg="[TESTER][UE] disableTunnel is false"
time="2025-08-31T06:27:48Z" level=info msg="[TESTER][GNB] Control interface IP/Port: 10.33.33.9:38412~"
time="2025-08-31T06:27:48Z" level=info msg="[TESTER][GNB] Data interface IP/Port: 10.33.33.9:2152"
time="2025-08-31T06:27:48Z" level=info msg="[TESTER][AMF] AMF IP/Port: 10.33.33.10:38412"
time="2025-08-31T06:27:48Z" level=info msg=---------------------------------------
...
time="2025-08-31T06:27:49Z" level=info msg="[UE][NAS] PDU address received: 10.45.0.2"
time="2025-08-31T06:27:50Z" level=info msg="[UE][GTP] Interface val1234567891 has successfully been configured for UE 10.45.0.2"
time="2025-08-31T06:27:50Z" level=info msg="[UE][GTP] You can do traffic for this UE using VRF vrf1234567891, eg:"
time="2025-08-31T06:27:50Z" level=info msg="[UE][GTP] sudo ip vrf exec vrf1234567891 iperf3 -c IPERF_SERVER -p PORT -t 9000"
```

Connect to the PacketRusher container and then to the VRF:
```bash
# connect to the PacketRusher container
docker exec -it packetrusher bash

# Use the VRF inside the PacketRusher container
ip vrf exec vrf1234567891 bash

# Test the UE connection
ping 8.8.8.8
```

## Command Line Options
To see all command options try:
```bash
$ ./packetrusher -help
NAME:
   packetrusher - A new cli application

USAGE:
   packetrusher [global options] command [command options]

COMMANDS:
   ue                                          Launch a gNB and a UE with a PDU Session
                                               For more complex scenario and features, use instead packetrusher multi-ue

   gnb                                         Launch only a gNB
   multi-ue-pdu, multi-ue                      
                                               Load endurance stress tests.
                                               Example for testing multiple UEs: multi-ue -n 5 
                                               This test case will launch N UEs. See packetrusher multi-ue --help

   custom-scenario, c                          
   amf-load-loop                               
                                               Test AMF responses in interval
                                               Example for generating 20 requests to AMF per second in interval of 20 seconds: amf-load-loop -n 20 -t 20

   Test availability of AMF, amf-availability  
                                               Test availability of AMF in interval
                                               Test availability of AMF in 20 seconds: amf-availability -t 20

   help, h                                     Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --config value  Configuration file path. (Default: ./config/config.yml)
   --help, -h      show help
```