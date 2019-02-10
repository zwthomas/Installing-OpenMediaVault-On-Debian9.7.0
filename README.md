# Installing OpenMediaVault on Intel NUC
Make sure you are on Debian 9 (Stretch) by running:
```
lsb_release -a
```

Create this file
```
nano /etc/apt/sources.list.d/openmediavault.list
```

Insert this line in the file:

```
deb [trusted=yes] http://packages.openmediavault.org/public arrakis main
```


Execute the following commands:
```
export LANG=C
export DEBIAN_FRONTEND=noninteractive
export APT_LISTCHANGES_FRONTEND=none
sudo apt-get update
sudo apt-get --allow-unauthenticated install openmediavault-keyring
sudo apt-get update
sudo apt-get --yes --auto-remove --show-upgraded \
    --allow-downgrades --allow-change-held-packages \
    --no-install-recommends \
    --option Dpkg::Options::="--force-confdef" \
    --option DPkg::Options::="--force-confold" \
    install postfix openmediavault
# Initialize the system and database.
sudo omv-initsystem
```
