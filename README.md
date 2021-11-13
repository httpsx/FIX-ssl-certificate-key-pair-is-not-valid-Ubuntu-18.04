# FIX-ssl-certificate-key-pair-is-not-valid-Ubuntu-18.04

#Fix "ssl certificate key pair is not valid"  Ubuntu 18.04 
#Vesta / Hestiacp

# 1. Check Openssl version ###

```
openssl version
```

> OpenSSL 1.1.1 11 Sep 2018   <- BAD VERSION
#
> Need install 1.1.1c  version

# 2. Install openssl 1.1.1c
```
sudo -s
apt install make gcc -y
cd /usr/local/src
wget https://www.openssl.org/source/openssl-1.1.1c.tar.gz
tar xvf openssl-1.1.1c.tar.gz
cd openssl-1.1.1c
./config -Wl,--enable-new-dtags,-rpath,'$(LIBRPATH)'
make
make install
```
# 3. Add line in "/etc/manpath.config"
`MANPATH_MAP     /usr/local/ssl/bin      /usr/local/ssl/man`

# 4. run mandb
```
mandb
```
# 5. Add in "/etc/environment"  
`/usr/local/ssl/bin:`

> example -> PATH="/usr/local/ssl/bin:...

# 6. Check Openssl version
```
openssl version 
```
> OpenSSL 1.1.1c  28 May 2019  <- Good version :)
#
>  Now you can install the ssl certificate.
