Btrfs hibernation script 

```bash
mkdir -p ~/.gc && cd ~/.gc && git clone --quiet https://github.com/pietryszak/fedora-hibernation.git && cd fedora-hibernation && chmod +x hibernation.sh after-restart.sh
```

### Before run script adjust your swap size
```bash
sudo sed -i 's/sudo fallocate --length 96GiB /swap/swapfile/sudo fallocate --length YOUR_SWAP_FILE_GiB /swap/swapfile/g' ~/.gc/fedora-hibernation/hibernation.sh && ./hibernation.sh
```
#### Redhat swap size recommendations

| RAM | Swap size (With Hibernation) |
| ------------- | ------------- |
| ⩽ 2 GB | 3 times the amount of RAM  |
| > 2 GB – 8 GB | 2 times the amount of RAM |
| > 8 GB – 64 GB | 1.5 times the amount of RAM |
| > 64 GB | Hibernation not recommended |

[Source](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/managing_storage_devices/getting-started-with-swap_managing-storage-devices)

## After automatic restart of PC after first script use second script (script restart PC once again)
```bash 
sh -c ~/.gc/fedora-hibernation/after-restart.sh
```

Based on @jorp solution and information on this [gist](https://gist.github.com/eloylp/b0d64d3c947dbfb23d13864e0c051c67) provided by @eloylp and comment by @miXwui.
