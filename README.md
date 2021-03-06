hs-honeypot - Honeypot Hidden Service system
============================================

This is a simple way to build honeypot system. These scripts deploy hidden services and setup nginx to log the traffic.

Tutorial
--------

- Install Tor (Latest version from the Tor Project repository)
- Generate torrc configuration for Tor

```sh
$ cp torrc /etc/tor/torcc
$ mkdir /var/lib/tor/hss/
$ chmod 777 /var/lib/tor/hss/
```

- Install nginx
- Generate nginx configuration

```sh
$ rm /etc/nginx/sites-available/default
$ cp hs /etc/nginx/sites-available/hs
$ ln -s /etc/nginx/sites-available/hs /etc/nginx/sites-enabled/hs
```

Finally, restart the services and your logging systems is ready.

```sh
$ service nginx restart
$ service tor restart
```

Furthermore, you can follow Hidden Service directories that these HSs are using. Install Stem from GitHub sources. Stem is a Python controller library for Tor. Like its predecessor, TorCtl, it uses Tor's control protocol to help developers program against the Tor process

```sh
$ python hsdir_logger.py
Tor is running version 0.2.5.9-rc (git-ec6adfb30fe8637b)
2014-10-22 14:09:59 : Action: REQUESTED, address: igt7jva3cko2wfav, directory: $50E1DE9D8A47B3507646E590EAFDFEB94A48FD4C~binar20140514, directory_fingerprint: 50E1DE9D8A47B3507646E590EAFDFEB94A48FD4C, directory_nickname: binar20140514, descriptor_id: kdct2pzz2jiaenvb5ga2emzg2fjskyta
2014-10-22 14:10:00 : Action: RECEIVED, address: igt7jva3cko2wfav, directory: $50E1DE9D8A47B3507646E590EAFDFEB94A48FD4C~binar20140514, directory_fingerprint: 50E1DE9D8A47B3507646E590EAFDFEB94A48FD4C, directory_nickname: binar20140514, descriptor_id: None
```

You can follow possible TCP traffic to selected ports.

```sh
$ ls -l /var/log/nginx/hs_logs/
```
