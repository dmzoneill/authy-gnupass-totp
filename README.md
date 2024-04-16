# pass-totp

### Basic setup
Symlink the file and mkae executable
```
sudo ln -s $PWD/totp /usr/local/bin/totp
chmod +x totp
```

Insert your totp's into totp/all
```
pass insert totp/all
```

Contents of the password entry should be similar to 
```
otpauth://totp/Facebook:user1?digits=6&secret=25WQDUTSG3VRWGXZMGZADZV4DW5WGPKG
otpauth://totp/Google:xx@gmail.comdigits=6&secret=SJXDTQTXN3UVR4TG2HNIMLPLKYGFMHJ4
otpauth://totp/Docker:user2?digits=6&secret=NC2BTBFSWF3N6FKMX24JFCKEYZVN2JMS
```
update it at any time with
```
pass edit totp/all
```

### Usage
Simply run
```
daoneill@fedora:~$ totp
Service    Username       TOTP Code   Next Code   Remainder
Airvpn     xx&yy          764350      996756      17 secs
GitHub     dmzoneill      530158      177402      17 secs
PyPI       lol            538759      902529      17 secs
```