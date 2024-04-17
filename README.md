# pass-totp

### Basic setup
Symlink the file and make executable
```bash
$ sudo ln -s $PWD/totp /usr/local/bin/totp
$ chmod +x totp
```

Insert your totp's into totp/all
```bash
$ pass insert totp/all
```

Contents of the password entry should be similar to 
```
otpauth://totp/Facebook:user1?digits=6&secret=25WQDUTSG3VRWGXZMGZADZV4DW5WGPKG
otpauth://totp/Google:xx@gmail.comdigits=6&secret=SJXDTQTXN3UVR4TG2HNIMLPLKYGFMHJ4
otpauth://totp/Docker:user2?digits=6&secret=NC2BTBFSWF3N6FKMX24JFCKEYZVN2JMS
```
update it at any time with
```bash
$ pass edit totp/all
```

### Usage
Simply run
```bash
$ totp
Service    Username       TOTP Code   Next Code   Remainder
Airvpn     xx&yy          764350      996756      17 secs
GitHub     dmzoneill      530158      177402      17 secs
PyPI       lol            538759      902529      17 secs
```

## Sync with authy

Get authy exporter 
```bash
$ go install github.com/alexzorin/authy/...@latest
```
Run it once and setup
```bash
$ go/bin/authy-export
```

Symlink sync file and make executable
```bash
$ sudo ln -s $PWD/sync /usr/local/bin/totp-sync
$ chmod +x sync
```

Run it
```bash
$ AUTHY_EXPORT_PASSWORD=yourpass
$ totp-sync
```