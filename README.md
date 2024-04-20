# authy-gnupass-totp

This solution migrates from authy desktop app to gnupass.\
it works by copying the totp lines to an entry in gpnupass called totp/all.\
The gnu pass entry consist of all your totp secrets, for all your accounts,\
in once place. I have created a sync script to update the pass entry.\
TOTP views conists of a bash script, curses and python gtk solutions.

## ToDo
- browser plugin

## Basic setup
Symlink the file and make executable
```bash
sudo ln -s $PWD/totp /usr/local/bin/totp
chmod +x totp
```

Insert your totp's into totp/all
```bash
pass insert totp/all
```

Contents of the password entry should be similar to
```bash
otpauth://totp/Facebook:user1?digits=6&secret=your_secret
otpauth://totp/Google:xx@gmail.comdigits=6&secret=your_secret
otpauth://totp/Docker:user2?digits=6&secret=your_secret
```
update it at any time with
```bash
pass edit totp/all
```

## Usage
Simply run
```bash
totp
Service    Username       TOTP Code   Next Code   Remainder
Airvpn     xx&yy          764350      996756      17 secs
GitHub     dmzoneill      530158      177402      17 secs
PyPI       lol            538759      902529      17 secs
```

## Sync with authy

Get authy exporter
```bash
go install github.com/alexzorin/authy/...@latest
```
Run it once and setup
```bash
go/bin/authy-export
```

Symlink sync file and make executable
```bash
sudo ln -s $PWD/sync /usr/local/bin/totp-sync
sudo ln -s $PWD/totp /usr/local/bin/totp
sudo ln -s $PWD/ctotp /usr/local/bin/ctotp
sudo ln -s $PWD/gtotp /usr/local/bin/gtotp
chmod +x sync
chmod +x ctotp
chmod +x gtotp
chmod +x totp
```

Run sync it
```bash
AUTHY_EXPORT_PASSWORD=yourpass
totp-sync
```

Bash static output
```bash
totp
```
![totp](https://raw.githubusercontent.com/dmzoneill/pass-totp/main/imgs/totp.png)

Bash Curses
```bash
ctotp
```
![ctotp](https://raw.githubusercontent.com/dmzoneill/pass-totp/main/imgs/ctotp.png)

PyGTK 4
```bash
gtotp
```
![gtotp](https://raw.githubusercontent.com/dmzoneill/pass-totp/main/imgs/gtotp.png)
