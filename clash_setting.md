env:

​	system: ubuntu 20.04

​	clash version: v1.14.0

# First

First of all `su root`

then, download the clash in `~/download/`

​	[Release v1.14.0 · Dreamacro/clash (github.com)](https://github.com/Dreamacro/clash/releases/tag/v1.14.0)

use commend `tar -xzvf `to tar the gz pkg

```bash
mkdir /opt/clash
cp ~/download/ /opt/clash/
chmod +x /opt/clashclash-linux-amd64
```



# make the import file

**download these files in `/opt/clash`**

1. config.yaml

   you should use the windows app `clash for windows(cfw) `and subscrib your point

   because your subscribe url maybe the format is wrong，you need to use the `cfw`to change the yaml file format.

   this is the url about `cfw`:[Release 2.15 · 2dust/clashN (github.com)](https://github.com/2dust/clashN/releases/tag/2.15)

   **ps: this writeup is writing for the windows user, rename your yaml file to `config.yaml`.**

2. Country.mmdb

   this file I download in this way:

   [xOS/Country.mmdb: Geoip MaxMind Database for china ip list! This is also an example of generating MaxMind Database! (github.com)](https://github.com/xOS/Country.mmdb)

```bash
gedit /opt/clash/config.yaml

port: 7890
socks-port: 7891
allow-lan: true
mode: Rule
log-level: info
external-controller: 127.0.0.1:9090
secret: "123456" #your passwd to sign in the clash gui
external-ui: /opt/clash/clash-dashboard
proxies:
	...
```



# set your ubuntu proxy

setting -> network -> proxy

follow the yaml file.



# set the clash-dashboard

[Dreamacro/clash-dashboard: web port of clash (github.com)](https://github.com/Dreamacro/clash-dashboard)

use the way to set the clash gui env

```
cp -r ./clash-dashboard /opt/clash
cd /opt/clash/
chmod +x ./clash-dashboard
```



# Go!!!!!

```
cd /opt/clash/
./clashclash-linux-amd64 -d .

#open another terminal
su root
cd /opt/clash/clash-dashboard
pnpm start
```

your brower should the proxy to follow the system proxy

done!

