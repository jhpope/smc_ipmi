# smc_ipmi Telegraf input plugin
Python script to parse the output of [SMCIPMITool](https://www.supermicro.com/en/solutions/management-software/ipmi-utilities) into the [InfluxDB line protocol](https://docs.influxdata.com/influxdb/latest/reference/syntax/line-protocol/). Intended to be run via Telegraf's [exec](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/exec) input plugin.

## Requirements
The SMCIPMITool [[download]](https://www.supermicro.com/SwDownload/SwSelect_Free.aspx?cat=IPMI) must be installed on the Telegraf host.

## Install
Clone this repo to the Telegraf host and configure Telegraf as shown below.

## Configuration

`/etc/telegraf/telegraf.conf`
```
[[inputs.exec]]
   commands["/path/to/smc_ipmi.py /path/to/SCMIPMITool '192.168.1.2' 'ipmi_user' 'ipmi_pw' 'F'"]

   data_format = "influx"
```

## Usage
```
usage: smc_ipmi.py [-h] path ip user password {C,F}

SMCIpmi input plugin

positional arguments:
  path        Path to SMCIpmi utility
  ip          IP address of Supermicro host
  user        Username
  password    Password
  {C,F}       Temperature unit to use

optional arguments:
  -h, --help  show this help message and exit
```
