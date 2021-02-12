![bash_unit CI](https://github.com/pforret/repeat/workflows/bash_unit%20CI/badge.svg)
![Shellcheck CI](https://github.com/pforret/repeat/workflows/Shellcheck%20CI/badge.svg)
![GH Language](https://img.shields.io/github/languages/top/pforret/repeat)
![GH stars](https://img.shields.io/github/stars/pforret/repeat)
![GH tag](https://img.shields.io/github/v/tag/pforret/repeat)
![GH License](https://img.shields.io/github/license/pforret/repeat)
[![basher install](https://img.shields.io/badge/basher-install-white?logo=gnu-bash&style=flat)](https://basher.gitparade.com/package/)

# repeat

![pforret/repeat](assets/repeat.jpg)
check a command/file repeatedly and be alerted when the output changes

## 🚀 Installation

with [basher](https://github.com/basherpm/basher)

	$ basher install pforret/repeat

or with `git`

	$ git clone https://github.com/pforret/repeat.git
	$ cd repeat
    $ ./repeat

## 🔥 Usage

```
Program: repeat 1.0.0 by peter@forret.com
Updated: Feb 12 15:49:50 2021
Description: repeat a command and be alerted when the output changes
Usage: repeat [-d] [-e] [-f] [-h] [-q] [-v] [-l <log_dir>] [-t <tmp_dir>] [-n <number>] [-w <wait>] <action> <command?>
Flags, options and parameters:
    -d|--diff        : [flag] diff the change in output instead of just showing the new output [default: off]
    -e|--erase       : [flag] erase last output (first call always shows up) [default: off]
    -f|--force       : [flag] do not ask for confirmation (always yes) [default: off]
    -h|--help        : [flag] show usage [default: off]
    -q|--quiet       : [flag] no output [default: off]
    -v|--verbose     : [flag] output more [default: off]
    -l|--log_dir <?> : [option] folder for log files   [default: /Users/pforret/log/repeat]
    -t|--tmp_dir <?> : [option] folder for temp files  [default: .tmp]
    -n|--number <?>  : [option] number of times to repeat the command  [default: 100]
    -w|--wait <?>    : [option] seconds to wait between repeating the command  [default: 5]
    <action>         : [parameter] action to perform: run/file
    <command>        : [parameter] command to repeat (optional)
                                  @github.com:pforret/repeat.git                                             
### TIPS & EXAMPLES
* use repeat run 'command -flag parameters' to repeat the command
  repeat run 'ping -c 1 www.website.com'
* use repeat file /path/file.txt to repeatedly check the file
  repeat -d file /var/log/errors.log
* use repeat check to check if this script is ready to execute and what values the options/flags are
  repeat check
* use repeat env to generate an example .env file
  repeat env > .env
* use repeat update to update to the latest version
  repeat update
```
## 🔁 Examples

* wait for a DNS change to happen

```bash
> repeat -e run "nslookup www.example.com"
     Run [nslookup example.com] (#1/100 @ 1 secs)
### Output changed at Fri Feb 12 15:36:28 CET 2021
### NEW OUTPUT
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   example.com
Address: 188.166.1.1

###
... Ran [nslookup example.com] (#6/100 @ 36 secs) - wait 5 seconds
```

* wait for a file to change

```bash
> repeat -d file /var/log/results.txt
     Check [/var/log/results.txt] (#5/100 @ 21 secs)
### File changed at Fri Feb 12 16:09:13 CET 2021
### FILE DIFF
5d4
< Error in line 4
###
... Check [/var/log/results.txt] (#8/100 @ 36 secs) - wait 5 seconds
```

## 📝 Acknowledgements

* script created with [bashew](https://github.com/pforret/bashew)

&copy; 2021 Peter Forret
